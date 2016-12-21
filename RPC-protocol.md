The RPC protocol accepts JSON http POST requests.  The following are RPC commands along with the responses that are expected.

## Account balance  
Returns how many rai is owned by **account**  
Request:  
`{  
  "action": "account_balance",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}`  
Response:  
`{  
  "balance": "10000"  
}`

## Account create  
Creates a new, random account in **wallet**  
Request:  
`{  
  "action": "account_create",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}`

## Account list  
Lists all the accounts inside **wallet**  
Request:  
`{  
  "action": "account_list",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "accounts" : [
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
  ]
}`

## Account move  
Moves **accounts** from **source** to **wallet**  
Request:  
`{  
  "action": "account_move",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "source": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "accounts" : [  
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
  ]  
}`  
Response:  
`{  
  "moved" : "1"
}`

## Account weight  
Returns the voting weight for **account**  
Request:  
`{  
  "action": "account_weight",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}`  
Response:  
`{  
  "weight": "10000"  
}`

## Available supply  
Returns how many rai are in the public supply  
Request:  
`{  
  "action": "available_supply"  
}`  
Response:  
`{  
  "available": "10000"  
}`

## Retrieve block  
Retrieves a json representation of **block**  
Request:  
`{  
  "action": "block",  
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "contents" : "{
    "type": "open",
    "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
    "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
    "source": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",
    "work": "0000000000000000",
    "signature": "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
}"
}`

## Block account  
Returns the account containing block  
Request:  
`{  
  "action": "block_account",  
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}`

## Block count  
Reports the number of blocks in the ledger  
Request:  
`{  
  "action": "block_count"  
}`  
Response:  
`{
  "count": "1000"  
}`

## Chain  
Returns a list of block hashes in the chain starting at **block** up to **count**  
Request:  
`{  
  "action": "chain",
  "block": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "count": "1"    
}`  
Response:  
`{    
  "blocks" : [  
  "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
  ]  
}`

## Frontiers  
Returns a list of pairs of account and block hash representing the head block starting at **account** up to **count**  
Request:  
`{  
  "action": "frontiers",
  "account": "xrb_1111111111111111111111111111111111111111111111111117353trpda",  
  "count": "1"    
}`  
Response:  
`{    
  "frontiers" : [  
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000", "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
  ]  
}`

## Frontier count  
Reports the number of accounts in the ledger  
Request:  
`{  
  "action": "frontier_count"  
}`  
Response:  
`{
  "count": "1000"  
}`

## History  
Reports send/receive information for a chain of blocks  
Request:  
`{  
  "action": "history",  
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "count": "10"
}`  
Response:  
`{
    "history": {
        "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F": {
            "type": "receive",
            "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
            "amount": "100000000000000000000000000000000"
        }
    } 
}`

## Mrai from raw    
Divide a raw amount down by the Mrai ratio.  
Request:  
`{  
  "action": "mrai_from_raw",  
  "amount": "1000000000000000000000000000000"
}`  
Response:  
`{  
  "amount": "1"  
}`

## Mrai to raw    
Multiply an Mrai amount by the Mrai ratio.  
Request:  
`{  
  "action": "mrai_to_raw",  
  "amount": "1"
}`  
Response:  
`{  
  "amount": "1000000000000000000000000000000"  
}`

## Krai from raw    
Divide a raw amount down by the krai ratio.  
Request:  
`{  
  "action": "krai_from_raw",  
  "amount": "1000000000000000000000000000"
}`  
Response:  
`{  
  "amount": "1"  
}`

## Krai to raw    
Multiply an krai amount by the krai ratio.  
Request:  
`{  
  "action": "krai_to_raw",  
  "amount": "1"
}`  
Response:  
`{  
  "amount": "1000000000000000000000000000"  
}`

## Rai from raw    
Divide a raw amount down by the rai ratio.  
Request:  
`{  
  "action": "rai_from_raw",  
  "amount": "1000000000000000000000000"
}`  
Response:  
`{  
  "amount": "1"  
}`

## Rai to raw    
Multiply an rai amount by the rai ratio.  
Request:  
`{  
  "action": "rai_to_raw",  
  "amount": "1"
}`  
Response:  
`{  
  "amount": "1000000000000000000000000"  
}`

## Keepalive  
Tells the node to send a keepalive packet to **address**:**port**  
Request:  
`{  
  "action": "keepalive",
  "address": "::ffff:192.168.1.1",
  "port": "1024"  
}`  
Response:  
`{      
}`

## Wallet change password  
Changes the password for **wallet** to **password**  
Request:  
`{  
  "action": "password_change",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "password": "test"  
}`  
Response:  
`{  
  "changed" : "1"
}`

## Wallet password enter  
Enters the **password** in to **wallet**  
Request:  
`{  
  "action": "password_enter",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "password": "test"  
}`  
Response:  
`{  
  "valid" : "1"
}`

## Wallet valid password  
Checks whether the password entered for **wallet** is valid  
Request:  
`{  
  "action": "password_valid",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "valid" : "1"
}`

## Payment begin  
Begin a new payment session.  Searches wallet for an account that's marked as available and has a 0 balance.  If one is found, the account number is returned and is marked as unavailable.  If no account is found, a new account is created, placed in the wallet, and returned.  
Request:  
`{  
  "action": "payment_begin",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}`  

## Payment init  
Marks all accounts in wallet as available for being used as a payment session.  
Request:  
`{  
  "action": "payment_init",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "status" : "Ready"  
}`  

## Payment end  
End a payment session.  Marks the account as available for use in a payment session. 
Request:  
`{  
  "action": "payment_end",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "wallet": "FFFD1BAEC8EC20814BBB9059B393051AAA8380F9B5A2E6B2489A277D81789EEE"  
}`  
Response:  
`{}`   

## Payment wait  
Wait for payment of 'amount' to arrive in 'account' or until 'timeout' milliseconds have elapsed.  
Request:  
`{  
  "action": "payment_wait",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "amount": "1",  
  "timeout": "1000"  
}`  
Response:  
`{  
  "status" : "success"  
}`  

## Process block  
Publish **block** to the network  
Request:  
`{  
  "action": "process",  
  "block": "{
    \"type\": \"open\",
    \"account\": \"xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000\",
    \"representative\": \"xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000\",
    \"source\": \"FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4\",
    \"work\": \"0000000000000000\",
    \"signature\": \"00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000\"
}"  
}`  
Response:  
`{  
}`

## Wallet representative  
Returns the default representative for **wallet**  
Request:  
`{  
  "action": "representative",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
}`  
Response:  
`{  
  "representative" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"
}`

## Wallet representative set  
Sets the default **representative** for **wallet**  
Request:  
`{  
  "action": "representative_set",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"
}`  
Response:  
`{  
}`

## Search pending  
Tells the node to look for pending blocks for any account in **wallet**  
Request:  
`{  
  "action": "search_pending",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
}`  
Response:  
`{
  "started": "1"  
}`

## Send  
Send **amount** from **source** in **wallet** to **destination**  
Request:  
`{  
  "action": "send",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "source": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "destination": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
  "amount": "1000000"  
}`  
Response:  
`{  
  "block": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`

## Stop node   
Request:  
`{  
  "action": "stop"  
}`  
Response:  
(none)

## Validate account number checksum  
Check whether **account** is a valid account number  
Request:  
`{  
  "action": "validate_account_number",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}`  
Response:  
`{  
  "valid" : "1"
}`

## Retrieve node versions 
Request:  
`{  
  "action": "version" 
}`  
Response:  
`{  
  "rpc_version" : "1",
  "store_version" : "2"
}`

## Retrieve online peers
Request:  
`{  
  "action": "peers" 
}`  
Response:  
`{
    "peers": {
        0: "[::ffff:172.17.0.1]:32841"
    } 
}`

## Wallet add key  
Add an adhoc private key **key** to **wallet**  
Request:  
`{  
  "action": "wallet_add",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "key": "34F0A37AAD20F4A260F0A5B3CB3D7FB50673212263E58A380BC10474BB039CE4"  
}`  
Response:  
`{  
  "account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"
}`

## Wallet contains  
Check whether **wallet** contains **account**  
Request:  
`{  
  "action": "wallet_contains",
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000" 
}`  
Response:  
`{  
  "exists" : "1"
}`

## Wallet create  
Creates a new random wallet id  
Request:  
`{  
  "action": "wallet_create" 
}`  
Response:  
`{  
  "wallet" : "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
}`

## Wallet destroy  
Destroys **wallet** and all contained accounts  
Request:  
`{  
  "action": "wallet_destroy",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
}`

## Wallet export  
Return a json representation of **wallet**  
Request:  
`{  
  "action": "wallet_export",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"   
}`  
Response:  
`{  
  "json" : "{\"0000000000000000000000000000000000000000000000000000000000000000\": \"0000000000000000000000000000000000000000000000000000000000000001\"}"
}`

## Work cancel
Stop generating **work** for block  
Request:  
`{  
    "action": "work_cancel",  
    "hash": "718CC2121C3E641059BC1C2CFC45666C99E8AE922F7A807B7D07B62C995D79E2"  
}`  
Response:  
`{  
}`  

## Work generate
Generates **work** for block  
Request:  
`{  
    "action": "work_generate",  
    "hash": "718CC2121C3E641059BC1C2CFC45666C99E8AE922F7A807B7D07B62C995D79E2"  
}`  
Response:  
`{  
    "work": "2bf29ef00786a6bc"  
}`  