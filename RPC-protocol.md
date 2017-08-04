The RPC protocol accepts JSON http POST requests.  The following are RPC commands along with the responses that are expected.

## Account balance  
Returns how many RAW is owned and how many have not yet been received by **account**  
Request:  
`{  
  "action": "account_balance",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}`  
Response:  
`{  
  "balance": "10000",  
  "pending": "10000"  
}`

## Account block count
Get number of blocks for a specific **account**  
Request:  
`{  
  "action": "account_block_count",  
  "account": "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3"  
}`  
Response:  
`{  
  "block_count" : "19"  
}`

## Account create  
_enable_control required_  
Creates a new account, insert next deterministic key in **wallet**  
Request:  
`{  
  "action": "account_create",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}`

## Account get
Get account number for the **public key**  
Request:  
`{  
  "action": "account_get",  
  "key": "3068BB1CA04525BB0E416C485FE6A67FD52540227D267CC8B6E8DA958A7FA039"  
}`  
Response:  
`{  
  "account" : "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3sxwjym5rx"  
}`

## Account history  
Reports send/receive information for a **account**  
Request:  
`{  
  "action": "account_history",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "count": "10"
}`  
Response:  
`{
    "history": [{
            "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
            "type": "receive",
            "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
            "amount": "100000000000000000000000000000000"
    }]
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
_enable_control required_  
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

## Account public key
Get the public key for **account**  
Request:  
`{  
  "action": "account_key",  
  "account" : "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3sxwjym5rx"  
}`  
Response:  
`{  
  "key": "3068BB1CA04525BB0E416C485FE6A67FD52540227D267CC8B6E8DA958A7FA039"  
}`


## Account remove
_enable_control required_  
Remove **account** from **wallet**  
Request:  
`{  
  "action": "account_remove",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "account": "xrb_39a73oy5ungrhxy5z5oao1xso4zo7dmgpjd4u74xcrx3r1w6rtazuouw6qfi"
}`  
Response:  
`{  
  "removed": "1"
}`

## Account representative  
Returns the representative for **account**  
Request:  
`{  
  "action": "account_representative",  
  "account": "xrb_39a73oy5ungrhxy5z5oao1xso4zo7dmgpjd4u74xcrx3r1w6rtazuouw6qfi"
}`  
Response:  
`{  
  "representative" : "xrb_16u1uufyoig8777y6r8iqjtrw8sg8maqrm36zzcm95jmbd9i9aj5i8abr8u5"
}`

## Account representative set  
_enable_control required_  
Sets the representative for **account** in **wallet**  
Request:  
`{  
  "action": "account_representative_set",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "account": "xrb_39a73oy5ungrhxy5z5oao1xso4zo7dmgpjd4u74xcrx3r1w6rtazuouw6qfi",  
  "representative" : "xrb_16u1uufyoig8777y6r8iqjtrw8sg8maqrm36zzcm95jmbd9i9aj5i8abr8u5"
}`  
Response:  
`{  
  "block": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
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

## Accounts balances  
Returns how many RAW is owned and how many have not yet been received by **accounts list**  
Request:  
`{  
  "action": "accounts_balances",  
  "accounts": ["xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000", "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7"]  
}`  
Response:  
`{  
  "balances" : {  
    "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000":  
    {  
      "balance": "10000",  
      "pending": "10000"  
    },  
    "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7":  
    {  
      "balance": "10000000",  
      "pending": "0"  
    }  
  }  
}`  

## Accounts frontiers  
Returns a list of pairs of account and block hash representing the head block for **accounts list**  
Request:  
`{  
  "action": "accounts_frontiers",  
  "accounts": ["xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3", "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7"]  
}`  
Response:  
`{  
  "frontiers" : {  
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": "791AF413173EEE674A6FCF633B5DFC0F3C33F397F0DA08E987D9E0741D40D81A",  
    "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7": "6A32397F4E95AF025DE29D9BF1ACE864D5404362258E06489FABDBA9DCCC046F"  
  }  
}`  

## Accounts pending  
Returns a list of block hashes which have not yet been received by these **accounts**  
Request:  
`{  
  "action": "accounts_pending",  
  "accounts": ["xrb_1111111111111111111111111111111111111111111111111117353trpda", "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3"],  
  "count": "1"
}`  
Response:  
`{  
  "blocks" : {  
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": ["142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D"],  
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": ["4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74"]  
  }  
}`  
### Optional "threshold"  
_version 7.9.1+_   
Returns a list of pending block hashes with amount more or equal to **threshold**   
Request:  
`{  
  "action": "accounts_pending",  
  "accounts": ["xrb_1111111111111111111111111111111111111111111111111117353trpda", "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3"],  
  "count": "1",  
  "threshold": "1000000000000000000000000"   
}`  
Response:  
`{  
  "blocks" : {
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": {    
        "142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D": "6000000000000000000000000000000"    
    },    
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": {    
        "4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74": "106370018000000000000000000000000"    
    }  
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


## Retrieve multiple blocks  
Retrieves a json representations of **blocks**  
Request:  
`{  
  "action": "blocks",  
  "hashes": ["000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"]  
}`  
Response:  
`{  
  "blocks" : {  
    "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F": "{  
      "type": "open",  
      "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
      "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
      "source": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",  
      "work": "0000000000000000",  
      "signature": "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"  
    }"
  }
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
Reports the number of blocks in the ledger and unchecked synchronizing blocks   
Request:  
`{  
  "action": "block_count"  
}`  
Response:  
`{
  "count": "1000",  
  "unchecked": "10"  
}`

## Bootstrap  
Initialize bootstrap to specific **IP address** and **port**   
Request:  
`{  
  "action": "bootstrap",  
  "address": "::ffff:138.201.94.249",  
  "port": "7075"  
}`  
Response:  
`{
  "success": ""  
}`

## Multi-connection bootstrap  
Initialize multi-connection bootstrap to random peers   
Request:  
`{  
  "action": "bootstrap_any"  
}`  
Response:  
`{
  "success": ""  
}`

## Chain  
Returns a list of block hashes in the account chain starting at **block** up to **count**  
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


## Deterministic key  
Derive deterministic keypair from **seed** based on **index**  
Request:  
`{  
  "action": "deterministic_key",
  "seed": "0000000000000000000000000000000000000000000000000000000000000000",  
  "index": "0"    
}`  
Response:  
`{  
  "private": "9F0E444C69F77A49BD0BE89DB92C38FE713E0963165CCA12FAF5712D7657120F",  
  "public": "C008B814A7D269A1FA3C6528B19201A24D797912DB9996FF02A1FF356E45552B",  
  "account": "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7"  
}`  

## Frontiers  
Returns a list of pairs of account and block hash representing the head block starting at **account** up to **count**  
Request:  
`{  
  "action": "frontiers",
  "account": "xrb_1111111111111111111111111111111111111111111111111111hifc8npp",  
  "count": "1"    
}`  
Response:  
`{    
  "frontiers" : {  
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
  }  
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
    "history": [{
            "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
            "type": "receive",
            "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
            "amount": "100000000000000000000000000000000"
    }]
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
_enable_control required_  
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

## Key create  
Generates a **adhoc random keypair**  
Request:  
`{  
  "action": "key_create"  
}`  
Response:  
`{  
  "private": "781186FB9EF17DB6E3D1056550D9FAE5D5BBADA6A6BC370E4CBB938B1DC71DA3",  
  "public": "3068BB1CA04525BB0E416C485FE6A67FD52540227D267CC8B6E8DA958A7FA039",  
  "account": "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3sxwjym5rx"  
}`  

## Key expand  
Derive public key and account number from **private key**  
Request:  
`{  
  "action": "key_expand",  
  "key": "781186FB9EF17DB6E3D1056550D9FAE5D5BBADA6A6BC370E4CBB938B1DC71DA3"  
}`  
Response:  
`{  
  "private": "781186FB9EF17DB6E3D1056550D9FAE5D5BBADA6A6BC370E4CBB938B1DC71DA3",  
  "public": "3068BB1CA04525BB0E416C485FE6A67FD52540227D267CC8B6E8DA958A7FA039",  
  "account": "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3sxwjym5rx"  
}`  

## Payment begin
Begin a new payment session. Searches wallet for an account that's marked as available and has a 0 balance. If one is found, the account number is returned and is marked as unavailable. If no account is found, a new account is created, placed in the wallet, and returned.  
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


## Receive  
_enable_control required_  
Receive pending **block** for **account** in **wallet**  
Request:  
`{  
  "action": "receive",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "block": "53EAA25CE28FA0E6D55EA9704B32604A736966255948594D55CBB05267CECD48"  
}`  
Response:  
`{  
  "block": "EE5286AB32F580AB65FD84A69E107C69FBEB571DEC4D99297E19E3FA5529547B"  
}`

## Receive minimum  
_enable_control required, version 7.9.1+_   
Returns receive minimum for node  
Request:  
`{  
  "action": "receive_minimum"  
}`  
Response:  
`{  
  "amount": "1000000000000000000000000"  
}`

## Receive minimum set  
_enable_control required, version 7.9.1+_   
Set **amount** as new receive minimum for node until restart  
Request:  
`{  
  "action": "receive_minimum_set",  
  "amount": "1000000000000000000000000000000"
}`  
Response:  
`{  
  "success": ""  
}`

## Representatives  
Returns a list of pairs of representative and its voting weight  
Request:  
`{  
  "action": "representatives"    
}`  
Response:  
`{    
  "representatives" : {  
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": "3822372327060170000000000000000000000",  
    "xrb_1111111111111111111111111111111111111111111111111awsq94gtecn": "30999999999999999999999999000000",  
    "xrb_114nk4rwjctu6n6tr6g6ps61g1w3hdpjxfas4xj1tq6i8jyomc5d858xr1xi": "0"  
  }  
}`

## Wallet representative  
Returns the default representative for **wallet**  
Request:  
`{  
  "action": "wallet_representative",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
}`  
Response:  
`{  
  "representative" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"
}`

## Wallet representative set  
_enable_control required_  
Sets the default **representative** for **wallet**  
Request:  
`{  
  "action": "wallet_representative_set",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"
}`  
Response:  
`{  
  "set": "1"
}`


## Republish  
Rebroadcast blocks starting at **hash** to the network    
Request:  
`{  
  "action": "republish",    
  "hash": "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948"    
}`  
Response:  
`{    
  "blocks": [   
     "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
     "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293"
  ]       
}`   
### Optional "sources"  
_version 7.9.1+_   
Additionally rebroadcast source chain blocks for receive/open up to **sources** depth   
Request:  
`{  
  "action": "republish",    
  "hash": "90D0C16AC92DD35814E84BFBCC739A039615D0A42A76EF44ADAEF1D99E9F8A35",    
  "sources": "2"   
}`  
Response:  
`{    
  "blocks": [   
      "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
      "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293",   
      "90D0C16AC92DD35814E84BFBCC739A039615D0A42A76EF44ADAEF1D99E9F8A35"   
  ]       
}`   


## Search pending  
_enable_control required_  
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


## Search pending for all wallets  
_enable_control required, version 7.9.1+_  
Tells the node to look for pending blocks for any account in all available wallets  
Request:  
`{  
  "action": "search_pending_all"
}`  
Response:  
`{
  "success": ""  
}`

## Send  
_enable_control required_  
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
_enable_control required_  
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


## Successors  
Returns a list of block hashes in the account chain ending at **block** up to **count**  
Request:  
`{  
  "action": "successors",
  "block": "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",  
  "count": "1"    
}`  
Response:  
`{    
  "blocks" : [  
  "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293"  
  ]  
}`

## Retrieve node versions 
Request:  
`{  
  "action": "version" 
}`  
Response:  
`{  
  "rpc_version" : "1",
  "store_version" : "2",
  "node_vendor" : "RaiBlocks 7.5.0"
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

## Pending  
Returns a list of block hashes which have not yet been received by this account.  
`{  
  "action": "pending",
  "account": "xrb_1111111111111111111111111111111111111111111111111117353trpda",  
  "count": "1"    
}`  
Response:  
`{    
  "blocks" : [ "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F" ]  
}`   
### Optional "threshold"  
_version 7.9.1+_   
Returns a list of pending block hashes with amount more or equal to **threshold**  
Request:  
`{  
  "action": "pending",  
  "account": "xrb_1111111111111111111111111111111111111111111111111117353trpda",  
  "count": "1",  
  "threshold": "1000000000000000000000000"   
}`  
Response:  
`{  
  "blocks" : {    
        "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F": "6000000000000000000000000000000"    
    }  
}`  

## Pending exists  
_version 7.9.1+_   
Check whether block is pending by **hash**  
Request:  
`{  
  "action": "pending_exists",
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F" 
}`  
Response:  
`{  
  "exists" : "1"
}`

## Wallet add key  
_enable_control required_  
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

## Wallet total balance  
Returns the sum of all accounts balances in **wallet**  
Request:  
`{  
  "action": "wallet_balance_total",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "balance": "10000",  
  "pending": "10000"  
}`

## Wallet accounts balances  
Returns how many rai is owned and how many have not yet been received by all accounts in **wallet**  
Request:  
`{  
  "action": "wallet_balances",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
  "balances" : {  
    "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000": {  
      "balance": "10000",  
      "pending": "10000"  
    }
  }   
}`

## Wallet change seed  
_enable_control required_  
Changes seed for **wallet** to **seed**  
Request:  
`{  
  "action": "wallet_change_seed",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "seed": "74F2B37AAD20F4A260F0A5B3CB3D7FB51673212263E58A380BC10474BB039CEE"  
}`  
Response:  
`{  
  "success" : ""
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
_enable_control required_  
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
_enable_control required_  
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

## Wallet frontiers  
Returns a list of pairs of account and block hash representing the head block starting for accounts from **wallet**  
Request:  
`{  
  "action": "wallet_frontiers",
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"    
}`  
Response:  
`{    
  "frontiers" : {  
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
  }  
}`

## Wallet pending  
_enable_control required, version 7.9.1+_   
Returns a list of block hashes which have not yet been received by accounts in this **wallet**  
Request:  
`{  
  "action": "wallet_pending",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"    
  "count": "1"
}`  
Response:  
`{  
  "blocks" : {  
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": ["142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D"],  
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": ["4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74"]  
  }  
}`  
### Optional "threshold"  
Returns a list of pending block hashes with amount more or equal to **threshold**   
Request:  
`{  
  "action": "wallet_pending",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"    
  "count": "1",  
  "threshold": "1000000000000000000000000"   
}`  
Response:  
`{  
  "blocks" : {
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": {    
        "142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D": "6000000000000000000000000000000"    
    },    
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": {    
        "4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74": "106370018000000000000000000000000"    
    }  
}`  

## Wallet republish  
_enable_control required, version 7.9.1+_   
Rebroadcast blocks for accounts from **wallet** starting at frontier down to **count** to the network     
Request:  
`{  
  "action": "wallet_republish",    
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "count": "2"   
}`  
Response:  
`{    
  "blocks": [   
      "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
      "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293",   
      "90D0C16AC92DD35814E84BFBCC739A039615D0A42A76EF44ADAEF1D99E9F8A35"   
  ]       
}`   


## Wallet work get
_enable_control required, version 7.9.1+_     
Returns a list of pairs of account and work from **wallet**   
Request:  
`{  
    "action": "wallet_work_get",  
    "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}`  
Response:  
`{  
   "works": {
       "xrb_1111111111111111111111111111111111111111111111111111hifc8npp": "432e5cf728c90f4f"   
   }
}`  

## Wallet change password  
_enable_control required_  
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

## Work cancel
_enable_control required_  
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
_enable_control required_  
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

## Work get
_enable_control required, version 7.9.1+_     
Retrieves work for **account** in **wallet**  
Request:  
`{  
    "action": "work_get",  
    "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
    "account": "xrb_1111111111111111111111111111111111111111111111111111hifc8npp"  
}`  
Response:  
`{  
    "work": "432e5cf728c90f4f"  
}`  

## Work set
_enable_control required, version 7.9.1+_     
Set **work** for **account** in **wallet**  
Request:  
`{  
    "action": "work_set",  
    "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
    "account": "xrb_1111111111111111111111111111111111111111111111111111hifc8npp",  
    "work": "0000000000000000"  
}`  
Response:  
`{  
    "success": ""  
}`  

## Work validate 
Check whether **work** is valid for block  
Request:  
`{  
    "action": "work_validate",  
    "work": "2bf29ef00786a6bc",  
    "hash": "718CC2121C3E641059BC1C2CFC45666C99E8AE922F7A807B7D07B62C995D79E2"  
}`  
Response:  
`{  
    "valid": "1"  
}`  

## RPC callback
Send JSON POST requests with every new block to callback server _http://callback_address:callback_port<callback_target>_ defined in [config.json](https://github.com/clemahieu/raiblocks/wiki/config.json).  
Sample:  
https://localhost:8080/  
`{  
    "account": "xrb_1m5cfk468k9cwfdp8zsiktc3dghxh6qabef7mno5odos9h91nn5wzs58g7st",  
    "hash": "B5678177F615A890C28F6716FBD81E1068ADAC27C85E00EDCCC21832CFF1C413",  
    "block": "{  
        "type": "send",  
        "previous": "F91264792342F6B99CC9B3C946726537EFA5F7C925CCCAB49C32B5B423CCB07B",  
        "destination": "xrb_39ymww61tksoddjh1e43mprw5r8uu1318it9z3agm7e6f96kg4ndqg9tuds4",  
        "balance": "000000015D47BE1FF551BFBBE1000000",  
        "work": "f57ec8eab4e3d760",  
        "signature": "DBD8ECA13CCDEC87FAE0E7B2AAA2460492249410A18E9C06AD454862260038D8B55ACD130F9C402C24ED3E97C579E33C82B93368156B8E0E4183CF7B45205B0A"  
    },  
    "amount": "1099000000000000000000000000000000"  
}`  