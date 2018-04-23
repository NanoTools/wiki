# NEP-01: Universal Blocks

The implementation of state blocks (known as "universal blocks") is a protocol improvement that encodes all account data in every transaction. This allows the following:

1. Simplifies account balance computation and block verification
2. Enables inexpensive hardware to easily and securely sign transactions
3. Aggressive pruning of the block-lattice

## Legacy Blocks
Previously, before the change to state blocks, there were 4 transaction types: open, send, receive, and change.

### Open
To create an account, you need to issue an *open* transaction. An open transaction is always the first transaction of every account-chain and can be created upon the first receipt of funds. The *account* field stores the public-key (address) derived from the private-key that is used for signing. The *source* field contains the hash of the transaction that sent the funds. On account creation, a representative must be chosen to vote on your behalf; this can be changed later with a *change* transaction. The account can declare itself as its own representative.

```
{
   account: DC04354B1...AE8FA2661B2,
   source: DC1E2B3F7C...182A0E26B4A,
   representative: xrb_1anr...posrs,
   work: 0000000000000000,
   type: open,
   signature: 83B0...006433265C7B204
}
```

### Send
To send from an address, the address must already have an existing open block. The *previous* field contains the hash of the previous block in the account-chain. The *destination* field contains the account for funds to be sent to. A send block is immutable once confirmed. Once broadcasted to the network, funds are immediately deducted from the balance of the sender's account and wait as *pending* until the receiving party signs a block to accept these funds. Pending funds should not be considered awaiting confirmation, as they are as good as spent from the sender's account and the sender cannot revoke the transaction.

```
{
   previous: 1967EA355...F2F3E5BF801,
   balance: 010a8044a0...1d49289d88c,
   destination: xrb_3w...m37goeuufdp,
   work: 0000000000000000,
   type: send,
   signature: 83B0...006433265C7B204
}
```

### Receive

To complete a transaction, the recipient of sent funds must create a receive block on their own account-chain. The source field references the hash of the associated send transaction. Once this block is created and broadcasted, the account's balance is updated and the funds have officially moved into their account.

```
{
   previous: DC04354B1...AE8FA2661B2,
   source: DC1E2B3F7C6...182A0E26B4A,
   work: 0000000000000000,
   type: receive,
   signature: 83B0...006433265C7B204
}
```

### Change

Account holders having the ability to choose a representative to vote on their behalf is a powerful decentralization tool that has no strong analog in Proof of Work or Proof of Stake protocols. In conventional PoS systems, the account owner's node must be running to participate in voting. Continuously running a node is impractical for many users; giving a representative the power to vote on an account's behalf relaxes this requirement. Account holders have the ability to reassign consensus to any account at any time. A *change* transaction changes the representative of an account by subtracting the vote weight from the old representative and adding the weight to the new representative. No funds are moved in this transaction, and the representative does not have spending power of the account's funds.

```
{
   previous: DC04354B1...AE8FA2661B2,
   representative: xrb_1anrz...posrs,
   work: 0000000000000000,
   type: change,
   signature: 83B0...006433265C7B204
}
```

## New State Blocks

The *state* block combines all 4 old transaction types into a single block. Because of this, the "type" of the block is simply "state".

| Key |Representation| Value Description |
| --- | -------------| ----------------- |
| previous       | 32-Byte HEX | Previous head block on account; 0 if *open* block. |
| Link           | 32-Byte HEX | Multipurpose Field; See Link Table below|
| representative | String | Representative xrb_ address. |
| account        | String | This account's xrb_ address. |
| balance        | Decimal String in Raw | Resulting balance |
| work           | 8-Byte Hex | Proof of Work Nonce. |
| signature      | 64-Byte HEX | ED25519+Blake2b 512-bit signature|

Depending on transaction intent, the "link" field is multipurpose for "block_create" rpc calls:

| Type | Value Description | Example Value |
| --- | ----------------- | ---------------|
| Open | (HEX) Pairing Send Block's Hash | F076D8F6254F089A8E66D0C934FA63D927F4458FC1D96815066D83B3658ABA26 |
| Change | (HEX) Must be 0 | 0000000000000000000000000000000000000000000000000000000000000000 |
| Send | (STR) Destination "xrb_" address | xrb_1utx843j4hgac1ixbtdygpayqcqho35oy3ufkfp19pj4rdb3sezqt975f8ae |
| Receive | (HEX) Pairing Send Block's Hash | F076D8F6254F089A8E66D0C934FA63D927F4458FC1D96815066D83B3658ABA26 |

In the completed, signed transaction json, the "link" field is *always* hexidecimal.

## rai_node RPC Calls
Since this is largely a backend change; most RPC commands will remain unchanged. One notable difference, however, is the "block_create" command for off-line signing.

If you would like to follow along; the values used in these examples are:
```
Seed:
168728029C60D62D37C6902FE9A3FFC78E9685A410EB3E937AEABAC2BE199689

Wallet ID:
557832FF41BAF4860ED4D7023E9ACE74F1427C3F8232B6AFFB491D98DD0EA1A2

Private Key:
B61AEB236B0C8A2DFDD71C06F1F3544C524801E4B45B7A34DFDEC6F74F177927

Public Key:
C1CD33D62CC72FAC1294C990D4DD2B02A4DB85D42F220C48C13AF288FB21D4C1

Address:
xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php
```

Do not use this seed for any account with funds. Your ``wallet_id`` value will be different.

These examples are assumed to be done in sequential order, and that the block is processed before the next example.

##### Example 1) Open
Address sends 1 raw to account  ``xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php``, which doesn't have an open block yet. Let us also assume that the send block hash was ``1EF0AD02257987B48030CC8D38511D3B2511672F33AF115AD09E18A86A8355A8``.

Here we will create an open block for ``xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php``, setting ``xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j`` as the representative, and receiving the above mentioned block.
Command:
```
curl -d '{
    "action":"block_create",
    "type":"state",
    "previous":"0",
    "account":"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php",
    "representative":"xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j",
    "balance":"1",
    "link":"1EF0AD02257987B48030CC8D38511D3B2511672F33AF115AD09E18A86A8355A8",
    "wallet":"557832FF41BAF4860ED4D7023E9ACE74F1427C3F8232B6AFFB491D98DD0EA1A2"
}' 

127.0.0.1:7076
```
Note that the balance field is in decimal ``raw``, and there are $$10^{30}$$ raw in 1 Nano.
Response:
```
{
    "hash": "FC5A7FB777110A858052468D448B2DF22B648943C097C0608D1E2341007438B0",
    "block": "{\n    \"type\": \"state\",\n    \"account\": \"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php\",\n    \"previous\": \"0000000000000000000000000000000000000000000000000000000000000000\",\n    \"representative\": \"xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j\",\n    \"balance\": \"1\",\n    \"link\": \"1EF0AD02257987B48030CC8D38511D3B2511672F33AF115AD09E18A86A8355A8\",\n    \"link_as_account\": \"xrb_19qion34cye9pk153m6f93ajtgs747mkyexh47ff39iro3oa8ofa43o4zwx4\",\n    \"signature\": \"593D865DDCC6018F197C0EACD15E5CED3DAF134EDFAF6553DB9C1D0E11DBDCBBE1B01E1A4C6D4378289567E59BA122DA5BFD49729AA6C2B0FC9E592A546B4F09\",\n    \"work\": \"0000000000000000\"\n}\n"
}
```
The only curious field in the response is "link_as_account". This is if the "link" field were to be interpreted as a 256-bit public key and translated into an xrb_ address. This field is only provided for convenience; when the completed block json is processed and broadcasted to the network, this field is stripped away. If you are creating and signing your own blocks external to rai_node, you do not need to include a "link_as_account" field.

##### Example 2) Receive
5 Nano is sent to ``xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php`` and that the send block hash was ``B2EC73C1F503F47E051AD72ECB512C63BA8E1A0ACC2CEE4EA9A22FE1CBDB693F``. The corresponding receive block on the account-chain would be:
```
curl -d '{
    "action":"block_create",
    "type":"state",
    "previous":"FC5A7FB777110A858052468D448B2DF22B648943C097C0608D1E2341007438B0",
    "account":"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php",
    "representative":"xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j",
    "balance":"5000000000000000000000000000001",
    "link":"B2EC73C1F503F47E051AD72ECB512C63BA8E1A0ACC2CEE4EA9A22FE1CBDB693F",
    "wallet":"557832FF41BAF4860ED4D7023E9ACE74F1427C3F8232B6AFFB491D98DD0EA1A2"
}' 127.0.0.1:7076
```
Here the balance is ``5000000000000000000000000000001`` because we originally had `1` raw in our account and now we are adding ``5000000000000000000000000000000`` to it.
Response:
```
{
    "hash": "597395E83BD04DF8EF30AF04234EAAFE0606A883CF4AEAD2DB8196AAF5C4444F",
    "block": "{\n    \"type\": \"state\",\n    \"account\": \"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php\",\n    \"previous\": \"FC5A7FB777110A858052468D448B2DF22B648943C097C0608D1E2341007438B0\",\n    \"representative\": \"xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j\",\n    \"balance\": \"5000000000000000000000000000001\",\n    \"link\": \"B2EC73C1F503F47E051AD72ECB512C63BA8E1A0ACC2CEE4EA9A22FE1CBDB693F\",\n    \"link_as_account\": \"xrb_3eqegh1zc1znhr4joosgsfakrrxtjrf1om3exs9cmajhw97xptbzi3kfba1j\",\n    \"signature\": \"90CBD62F5466E35DB3BFE5EFDBC6283BD30C0591A3787C9458D11F2AF6188E45E6E71B5F4A8E3598B1C80080D6024867878E355161AD1935CD757477991D3B0B\",\n    \"work\": \"0000000000000000\"\n}\n"
}
```

##### Example 3) Send
Now our account ``xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php`` wants to send 2 Nano to ``xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p``.
Command:
```
curl -d '{
    "action":"block_create",
    "type":"state",
    "previous":"597395E83BD04DF8EF30AF04234EAAFE0606A883CF4AEAD2DB8196AAF5C4444F",
    "account":"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php",
    "representative":"xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j",
    "balance":"3000000000000000000000000000001",
    "link":"xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p",
    "wallet":"557832FF41BAF4860ED4D7023E9ACE74F1427C3F8232B6AFFB491D98DD0EA1A2"
}' 127.0.0.1:7076
```
Response:
```
{
    "hash": "128106287002E595F479ACD615C818117FCB3860EC112670557A2467386249D4",
    "block": "{\n    \"type\": \"state\",\n    \"account\": \"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php\",\n    \"previous\": \"597395E83BD04DF8EF30AF04234EAAFE0606A883CF4AEAD2DB8196AAF5C4444F\",\n    \"representative\": \"xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j\",\n    \"balance\": \"3000000000000000000000000000001\",\n    \"link\": \"5C2FBB148E006A8E8BA7A75DD86C9FE00C83F5FFDBFD76EAA09531071436B6AF\",\n    \"link_as_account\": \"xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p\",\n    \"signature\": \"D7975EE2F6FAE1FC7DA336FB9DD5F7E30FC1A6825021194E614F0588073D1A4901E34E3CAE8739F1DE2FD85A73D2A0B26F8BE6539E0548C9A45E1C1887BFFC05\",\n    \"work\": \"0000000000000000\"\n}\n"
}
```
Because the account balance changed from ``5000000000000000000000000000001`` raw to ``3000000000000000000000000000001`` raw, the block is interpreted as a send. The "link" field is populated with the public key of  ``xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p``.

##### Example 4) Change Representative
To change our representative to ``xrb_1anrzcuwe64rwxzcco8dkhpyxpi8kd7zsjc1oeimpc3ppca4mrjtwnqposrs``.
```
curl -d '{
    "action":"block_create",
    "type":"state",
    "previous":"128106287002E595F479ACD615C818117FCB3860EC112670557A2467386249D4",
    "account":"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php",
    "representative":"xrb_1anrzcuwe64rwxzcco8dkhpyxpi8kd7zsjc1oeimpc3ppca4mrjtwnqposrs",
    "balance":"3000000000000000000000000000001",
    "link":"0000000000000000000000000000000000000000000000000000000000000000",
    "wallet":"557832FF41BAF4860ED4D7023E9ACE74F1427C3F8232B6AFFB491D98DD0EA1A2"
}' 127.0.0.1:7076
```
Response:
```
{
    "hash": "2A322FD5ACAF50C057A8CF5200A000CF1193494C79C786B579E0B4A7D10E5A1E",
    "block": "{\n    \"type\": \"state\",\n    \"account\": \"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php\",\n    \"previous\": \"128106287002E595F479ACD615C818117FCB3860EC112670557A2467386249D4\",\n    \"representative\": \"xrb_1anrzcuwe64rwxzcco8dkhpyxpi8kd7zsjc1oeimpc3ppca4mrjtwnqposrs\",\n    \"balance\": \"3000000000000000000000000000001\",\n    \"link\": \"0000000000000000000000000000000000000000000000000000000000000000\",\n    \"link_as_account\": \"xrb_1111111111111111111111111111111111111111111111111111hifc8npp\",\n    \"signature\": \"7E9A7B368DBEB280B01C22633DC82F6CEF00F529E07B76A0232614D2BCDAF85BF52AC9DA4DBE4468B6F144CE82F2FDE44080C8363F903A6EC3D999252CB1E801\",\n    \"work\": \"0000000000000000\"\n}\n"
}
```
Note that the "link" field is all 0's. As another sanity check, we notice the all 0 public key gets translated into the burn address ``xrb_1111111111111111111111111111111111111111111111111111hifc8npp``.

##### Example 5) Change Representative & Send
You can change your representative while performing a send or receive. Let us send 3 more Nano to ``xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p``. Let us also revert back and make ``xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j`` our representative again.
Command:
```
curl -d '{
    "action":"block_create",
    "type":"state",
    "previous":"2A322FD5ACAF50C057A8CF5200A000CF1193494C79C786B579E0B4A7D10E5A1E",
    "account":"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php",
    "representative":"xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j",
    "balance":"1",
    "link":"xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p",
    "wallet":"557832FF41BAF4860ED4D7023E9ACE74F1427C3F8232B6AFFB491D98DD0EA1A2"
}' 127.0.0.1:7076
```
Response:
```
{
    "hash": "9664412A834F0C27056C7BC4A363FBAE86DF8EF51341A5A5EA14061727AE519F",
    "block": "{\n    \"type\": \"state\",\n    \"account\": \"xrb_3igf8hd4sjshoibbbkeitmgkp1o6ug4xads43j6e4gqkj5xk5o83j8ja9php\",\n    \"previous\": \"2A322FD5ACAF50C057A8CF5200A000CF1193494C79C786B579E0B4A7D10E5A1E\",\n    \"representative\": \"xrb_3p1asma84n8k84joneka776q4egm5wwru3suho9wjsfyuem8j95b3c78nw8j\",\n    \"balance\": \"1\",\n    \"link\": \"5C2FBB148E006A8E8BA7A75DD86C9FE00C83F5FFDBFD76EAA09531071436B6AF\",\n    \"link_as_account\": \"xrb_1q3hqecaw15cjt7thbtxu3pbzr1eihtzzpzxguoc37bj1wc5ffoh7w74gi6p\",\n    \"signature\": \"4D388F982188E337D22E0E66CD24BCABD09BED1E920940C453039B55B6A4724D7BD106019AACC1840480938FF4FA024F041E6E6A32B3641C28E0262025020B03\",\n    \"work\": \"0000000000000000\"\n}\n"
}
```

## Hash order for signing
If you choose to implement your own signing; the order of data (in bytes) to hash prior to signing is as follows. The State Block Preamble is 32 bytes and has value ``0x6``. All values are binary representations, no ASCII/UTF-8 strings.
1) State Block Preamble (32-Bytes)
2) account (32-Bytes)
3) previous (32-Bytes)
4) representative (32-Bytes)
5) balance (16-Bytes)
6) link (32-Bytes)

The digital signing algorithm (which internally applies another Blake2b hashing) is applied on the resulting digest. Make sure that your private key uses the correct partnering public key while signing; signing with an incorrect public key may leak information about your private key.

## Deployment
State Blocks began deployment in v11 of the rai_node software. The update procedure was conducted via two canary blocks:

| Hash | Function |
| ---- | ---------|
| 89F1C0AC4C5AD23964AB880571E3EA67FDC41BD11AB20E67F0A29CF94CD4E24A | Begin State-Block Parsing |
| B6DC4D64801BEC7D81DAA086A5733D251E8CBA0E9226FD6173D97C0569EC2998" | Begin State-Block Generation |

Once State-Blocks are used on an account-chain, legacy blocks can no longer be added to that account chain. State-blocks can still interact (e.g. receive funds) with legacy blocks.
## Benefits

#### Hardware Wallet
Previously it was impractical for a hardware wallet to securely sign a send transaction amount since the account balance may not have yet been encoded into the account chain. Now only the previous head block and the new transaction data is required to trustlessly sign transactions on a hardware wallet:
1. Computer sends head account block to wallet.
2. Wallet then computes the head block hash
3. Computer sends over new transaction metadata (may or may not include the PoW)
4. Wallet verifies the "previous" field matches the hash computed in part 3
5. If the Representative changes from previous block, prompt user
6. Prompt user on transaction value if "balance" difference between blocks is non-zero
7. Sign transaction and send back to computer to be broadcasted

#### Pruning
Since the latest headblock contains the complete current state of an account, all previous blocks can be deleted without loss in account state. This will decrease disk usage, speed up database search, and lower hardware requirements for pruned nodes.

