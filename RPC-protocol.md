The RPC protocol accepts JSON http POST requests.  The following are RPC commands along with the responses that are expected.

## Account balance  
Returns how many rai is owned by **account**  
Request:  
`{  
  "action": "account_balance",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
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
  "account" : "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
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
  "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
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
  "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
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
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`  
Response:  
`{  
  "weight": "10000"  
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
    "account": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",
    "representative": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",
    "source": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",
    "work": "0000000000000000",
    "signature": "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
}"
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
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8",  
  "count": "1"    
}`  
Response:  
`{    
  "frontiers" : [  
  "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8", "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
  ]  
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
  "action": "password_valid"  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
}`  
Response:  
`{  
  "valid" : "1"
}`

## Process block  
Publish **block** to the network  
Request:  
`{  
  "action": "process",  
  "block": "{
    \"type\": \"open\",
    \"account\": \"FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4\",
    \"representative\": \"FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4\",
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
  "representative" : "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"
}`

## Wallet representative set  
Sets the default **representative** for **wallet**  
Request:  
`{  
  "action": "representative_set",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "representative": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"
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
  "source": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8",  
  "destination": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8",
  "amount": "1000000"  
}`  
Response:  
`{  
  "sent": "1"  
}`

## Validate account number checksum  
Check whether **account** is a valid account number  
Request:  
`{  
  "action": "validate_account_number",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
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

## Wallet add  
Add private key **key** to **wallet**  
Request:  
`{  
  "action": "wallet_add",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "key": "34F0A37AAD20F4A260F0A5B3CB3D7FB50673212263E58A380BC10474BB039CE4"  
}`  
Response:  
`{  
  "account" : "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"
}`

## Wallet contains  
Check whether **wallet** contains **account**  
Request:  
`{  
  "action": "wallet_contains",
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8" 
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