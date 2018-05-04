The RPC protocol accepts JSON HTTP POST requests. The following are RPC commands along with the responses that are expected.

## Overview
* Accounts
    * [Account balance](#account-balance)
    * [Account block count](#account-block-count)
    * [Account create](#account-create)
    * [Account get](#account-get)
    * [Account history](#account-history)
    * [Account information](#account-information)
    * [Account list](#account-list)
    * [Account move](#account-move)
    * [Account public key](#account-public-key)
    * [Account remove](#account-remove)
    * [Account representative set](#account-representative-set)
    * [Account representative](#account-representative)
    * [Account weight](#account-weight)
    * [Accounts balances](#accounts-balances)
    * [Accounts create](#accounts-create)
    * [Accounts frontiers](#accounts-frontiers)
    * [Accounts pending](#accounts-pending)
    * [Validate account number checksum](#validate-account-number-checksum)
* Blocks
    * [Block account](#block-account)
    * [Block count by type](#block-count-by-type)
    * [Block count](#block-count)
    * [Chain](#chain)
    * [Offline signing (create block)](#offline-signing--create-block)
    * [Process block](#process-block)
    * [Retrieve block](#retrieve-block)
    * [Retrieve multiple blocks with additional info](#retrieve-multiple-blocks-with-additional-info)
    * [Retrieve multiple blocks](#retrieve-multiple-blocks)
* Bootstrap
    * [Bootstrap](#bootstrap)
    * [Multi-connection bootstrap](#multi-connection-bootstrap)
* Conversion
    * [Krai from raw](#krai-from-raw)
    * [Krai to raw](#krai-to-raw)
    * [Mrai from raw](#mrai-from-raw)
    * [Mrai to raw](#mrai-to-raw)
    * [Rai from raw](#rai-from-raw)
    * [Rai to raw](#rai-to-raw)
* Confirmation
    * [Confirm block](#block-confirm)
    * [Confirmation history](#confirmation-history)
* Delegators
    * [Delegators](#delegators)
    * [Delegators count](#delegators-count) 
* Frontiers
    * [Frontiers](#frontiers)
    * [Frontier count](#frontier-count)
* Keys
    * [Deterministic key](#deterministic-key)
    * [Key create](#key-create)
    * [Key expand](#key-expand)
* Ledger
    * [History](#history)
    * [Ledger](#ledger)
    * [Successors](#successors)
* Network
    * [Available supply](#available-supply)
    * [Keepalive](#keepalive)
    * [Republish](#republish)
* Node
    * [Retrieve node versions](#retrieve-node-versions)
    * [Stop node](#stop-node)
* Payments
    * [Payment begin](#payment-begin)
    * [Payment end](#payment-end)
    * [Payment init](#payment-init)
    * [Payment wait](#payment-wait)
* Peers 
Conversations
Important and unread
 

    * [Add work peer](#add-work-peer)
    * [Clear work peers](#clear-work-peers)
    * [Retrieve online peers](#retrieve-online-peers)
    * [Retrieve work peers](#retrieve-work-peers)
* Pending
    * [Pending](#pending)
    * [Pending exists](#pending-exists)
    * [Search pending](#search-pending)
    * [Search pending for all wallets](#search-pending-for-all-wallets)
* Proof of Work
    * [Work cancel](#work-cancel)
    * [Work generate](#work-generate)
    * [Work get](#work-get)
    * [Work set](#work-set)
    * [Work validate](#work-validate)
* Receiving
    * [Receive](#receive)
    * [Receive minimum](#receive-minimum)
    * [Receive minimum set](#receive-minimum-set)
* Representatives
    * [Representatives](#representatives)
    * [Representatives online](#representatives-online)
    * [Wallet representative](#wallet-representative)
    * [Wallet representative set](#wallet-representative-set)
* Sending
    * [Send](#send)
* Statistics
    * [Statistics query](#statistics)
* Unchecked blocks
    * [Clear unchecked blocks](#clear-unchecked-blocks)
    * [Retrieve unchecked block](#retrieve-unchecked-block)
    * [Unchecked blocks with database keys](#unchecked-blocks-with-database-keys)
    * [Unchecked blocks](#unchecked-blocks)
* Wallet
    * [Wallet accounts balances](#wallet-accounts-balances)
    * [Wallet add key](#wallet-add-key)
    * [Wallet add watch-only accounts](#wallet-add-watch-only-accounts)
    * [Wallet change password](#wallet-change-password)
    * [Wallet change seed](#wallet-change-seed)
    * [Wallet contains](#wallet-contains)
    * [Wallet create](#wallet-create)
    * [Wallet destroy](#wallet-destroy)
    * [Wallet export](#wallet-export)
    * [Wallet frontiers](#wallet-frontiers)
    * [Wallet ledger](#wallet-ledger)
    * [Wallet lock](#wallet-lock)
    * [Wallet locked check](#wallet-locked-check)
    * [Wallet password enter (unlock wallet)](#wallet-password-enter-unlock-wallet)
    * [Wallet pending](#wallet-pending)
    * [Wallet representative set](#wallet-representative-set)
    * [Wallet representative](#wallet-representative)
    * [Wallet republish](#wallet-republish)
    * [Wallet total balance](#wallet-total-balance)
    * [Wallet valid password](#wallet-valid-password)
    * [Wallet work get](#wallet-work-get)
* [RPC callback](#rpc-callback)
 
## Account balance  
Returns how many RAW is owned and how many have not yet been received by **account**  
Request:
```  
{  
  "action": "account_balance",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}
```

Response:  
```
{  
  "balance": "10000",  
  "pending": "10000"  
}
```

## Account block count
Get number of blocks for a specific **account**  
Request:  
```
{  
  "action": "account_block_count",  
  "account": "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3"  
}
```

Response:  
```
{  
  "block_count" : "19"  
}
```

## Account information
Returns frontier, open block, change representative block, balance, last modified timestamp from local database & block count for **account**. Only works for accounts that have an entry on the ledger, will return "Account not found" otherwise.  

Request:  
```
{  
  "action": "account_info",  
  "account": "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3"  
}
```

Response:  
```
{  
    "frontier": "FF84533A571D953A596EA401FD41743AC85D04F406E76FDE4408EAED50B473C5",   
    "open_block": "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
    "representative_block": "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
    "balance": "235580100176034320859259343606608761791",   
    "modified_timestamp": "1501793775",   
    "block_count": "33"   
}
```

### Optional "representative", "weight", "pending"  
_version 9.0+_   
Additionally returns representative, voting weight, pending balance for account   
Request:  
```
{  
  "action": "account_info",  
  "account": "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3",    
  "representative": "true",  
  "weight": "true",  
  "pending": "true"  
}
```

Response:  
```
{  
    "frontier": "FF84533A571D953A596EA401FD41743AC85D04F406E76FDE4408EAED50B473C5",   
    "open_block": "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
    "representative_block": "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
    "balance": "235580100176034320859259343606608761791",   
    "modified_timestamp": "1501793775",   
    "block_count": "33",   
    "representative": "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3",   
    "weight": "1105577030935649664609129644855132177",   
    "pending": "2309370929000000000000000000000000"   
}
```

## Account create  
_enable_control required_  
Creates a new account, insert next deterministic key in **wallet**  
Request:  
```
{  
  "action": "account_create",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```
  
Response:  
```
{  
  "account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}
```

### Optional disabling work generation  
_version 9.0+_  
Disables work generation after creating account  
Request:  
```
{  
  "action": "account_create",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "work": "false"  
}
```

## Account get
Get account number for the **public key**  
Request:  
```
{  
  "action": "account_get",  
  "key": "3068BB1CA04525BB0E416C485FE6A67FD52540227D267CC8B6E8DA958A7FA039"  
}
```

Response:  
```
{  
  "account" : "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3sxwjym5rx"  
}
```

## Account history  

Reports send/receive information for an account. Change blocks are skipped, open blocks will appear as receive (unless raw is set to true - see optional parameters below). Response will start with the latest block for the account (the frontier), and will list all blocks back to the open block of this account when "count" is set to "-1".

Request:  
```
{  
  "action": "account_history",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "count": "1"
}
```

Response:  
```
{
    "history": [{
            "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
            "type": "receive",
            "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
            "amount": "100000000000000000000000000000000"
    }]
}
```

If the `count` limit results in stopping before the end of the account chain, then the response will also contain a `previous` field (outside of the `history` field) which contains the block hash that would be next to process if `count` was larger.

Optional parameters:

- `raw`: if set to `true` instead of the default `false`, instead of outputting a simplified send or receive explanation of blocks (intended for wallets), output all parameters of the block itself as seen in block_create or other APIs returning blocks. It still includes the "account" and "amount" properties you'd see without this option.  State/universal blocks in the raw history will also have a `subtype` field indicating their equivalent "old" block. Unfortunately, the "account" parameter for open blocks is the account of the source block, not the account of the open block, to preserve similarity with the non-raw history.
- `head`: instead of using the latest block for a specified account, use this block as the head of the account instead. Useful for pagination.

## Account list  
Lists all the accounts inside **wallet**  
Request:  
```
{  
  "action": "account_list",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "accounts" : [
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
  ]
}
```

## Account move  
_enable_control required_  
Moves **accounts** from **source** to **wallet**  
Request:  
```
{  
  "action": "account_move",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "source": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "accounts" : [  
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
  ]  
}
```  
Response:  
```
{  
  "moved" : "1"
}
```

## Account public key
Get the public key for **account**  
Request:  
```
{  
  "action": "account_key",  
  "account" : "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3sxwjym5rx"  
}
```  
Response:  
```
{  
  "key": "3068BB1CA04525BB0E416C485FE6A67FD52540227D267CC8B6E8DA958A7FA039"  
}
```


## Account remove
_enable_control required_  
Remove **account** from **wallet**  
Request:  
```
{  
  "action": "account_remove",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "account": "xrb_39a73oy5ungrhxy5z5oao1xso4zo7dmgpjd4u74xcrx3r1w6rtazuouw6qfi"
}
```  
Response:  
```
{  
  "removed": "1"
}
```

## Account representative  
Returns the representative for **account**  
Request:  
```
{  
  "action": "account_representative",  
  "account": "xrb_39a73oy5ungrhxy5z5oao1xso4zo7dmgpjd4u74xcrx3r1w6rtazuouw6qfi"
}
```  
Response:  
```
{  
  "representative" : "xrb_16u1uufyoig8777y6r8iqjtrw8sg8maqrm36zzcm95jmbd9i9aj5i8abr8u5"
}
```

## Account representative set  
_enable_control required_  
Sets the representative for **account** in **wallet**  
Request:  
```
{  
  "action": "account_representative_set",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "account": "xrb_39a73oy5ungrhxy5z5oao1xso4zo7dmgpjd4u74xcrx3r1w6rtazuouw6qfi",  
  "representative" : "xrb_16u1uufyoig8777y6r8iqjtrw8sg8maqrm36zzcm95jmbd9i9aj5i8abr8u5"
}
```  
Response:  
```
{  
  "block": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
}
```
### Optional "work"  
_version 9.0+_  
Uses **work** value for block from external source  

## Account weight  
Returns the voting weight for **account**  
Request:  
```
{  
  "action": "account_weight",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}
```  
Response:  
```
{  
  "weight": "10000"  
}
```

## Accounts balances  
Returns how many RAW is owned and how many have not yet been received by **accounts list**  
Request:  
```
{  
  "action": "accounts_balances",  
  "accounts": ["xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000", "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7"]  
}
```  
Response:  
```
{  
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
}
```  

## Accounts create  
_enable_control required, version 9.0+_  
Creates new accounts, insert next deterministic keys in **wallet** up to **count**  
Request:  
```
{  
  "action": "accounts_create",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "count": "2"
}
```  
Response:  
```
{  
  "accounts": [    
     "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",   
     "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3s00000000"
  ]   
}
```
### Optional enabling work generation  
_version 11.2+_  
Enables work generation after creating accounts  
Request:  
```
{  
  "action": "accounts_create",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "count": "2",  
  "work": "true"  
}
```  
***Note:*** Before version 11.2 work generation was enabled by default, if you want to disable work generation for previous versions, use "work": "false"    

## Accounts frontiers  
Returns a list of pairs of account and block hash representing the head block for **accounts list**  
Request:  
```
{  
  "action": "accounts_frontiers",  
  "accounts": ["xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3", "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7"]  
}
```  
Response:  
```
{  
  "frontiers" : {  
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": "791AF413173EEE674A6FCF633B5DFC0F3C33F397F0DA08E987D9E0741D40D81A",  
    "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7": "6A32397F4E95AF025DE29D9BF1ACE864D5404362258E06489FABDBA9DCCC046F"  
  }  
}
```  

## Accounts pending  
Returns a list of block hashes which have not yet been received by these **accounts**  
Request:  
```
{  
  "action": "accounts_pending",  
  "accounts": ["xrb_1111111111111111111111111111111111111111111111111117353trpda", "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3"],  
  "count": 1
}
```  
Response:  
```
{  
  "blocks" : {  
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": ["142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D"],  
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": ["4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74"]  
  }  
}
```  
### Optional "threshold"  
_version 8.0+_   
Returns a list of pending block hashes with amount more or equal to **threshold**   
Request:  
```
{  
  "action": "accounts_pending",  
  "accounts": ["xrb_1111111111111111111111111111111111111111111111111117353trpda", "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3"],  
  "count": "1",  
  "threshold": "1000000000000000000000000"   
}
```  
Response:  
```
{  
  "blocks" : {
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": {    
        "142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D": "6000000000000000000000000000000"    
    },    
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": {    
        "4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74": "106370018000000000000000000000000"    
    }  
}
```  
### Optional "source"  
_version 9.0+_   
Returns a list of pending block hashes with amount and source accounts   
Request:  
```
{  
  "action": "accounts_pending",  
  "accounts": ["xrb_1111111111111111111111111111111111111111111111111117353trpda", "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3"],  
  "count": "1",  
  "source": "true"   
}
```  
Response:  
```
{  
  "blocks" : {
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": {    
        "142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D": {   
             "amount": "6000000000000000000000000000000",       
             "source": "xrb_3dcfozsmekr1tr9skf1oa5wbgmxt81qepfdnt7zicq5x3hk65fg4fqj58mbr"
        }
    },    
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": {    
        "4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74": {   
             "amount": "106370018000000000000000000000000",       
             "source": "xrb_13ezf4od79h1tgj9aiu4djzcmmguendtjfuhwfukhuucboua8cpoihmh8byo"
        }   
    }  
}
```  

## Available supply  
Returns how many rai are in the public supply  
Request:  
```
{  
  "action": "available_supply"  
}
```  
Response:  
```
{  
  "available": "10000"  
}
```

## Retrieve block  
Retrieves a json representation of **block**  
Request:  
```
{  
  "action": "block",  
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "contents" : "{
    "type": "open",
    "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
    "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
    "source": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",
    "work": "0000000000000000",
    "signature": "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
}"
}
```

Note: The `Balance` is a uint128. However, it will be a hex-encoded (like `0000000C9F2C9CD04674EDEA40000000` for [1 Mxrb](https://github.com/nanocurrency/raiblocks/wiki/Distribution,-Mining-and-Units)) when the block is a *Send Block*. If the block is a *State-Block*, the same `Balance` will be a numeric-string (like `1000000000000000000000000000000`).

## Retrieve multiple blocks  
Retrieves a json representations of **blocks**  
Request:  
```
{  
  "action": "blocks",  
  "hashes": ["000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"]  
}
```  
Response:  
```
{  
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
}
```

## Retrieve multiple blocks with additional info   
Retrieves a json representations of **blocks** with transaction **amount** & block **account** 
Request:  
```
{  
  "action": "blocks_info",  
  "hashes": ["000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"]  
}
```  
Response:  
```
{  
  "blocks" : {   
    "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F": {   
       "block_account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",   
       "amount": "1000000000000000000000000000000",   
       "contents": "{  
          "type": "open",  
          "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
          "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
          "source": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",  
          "work": "0000000000000000",  
          "signature": "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"  
         }"
     }
  }
}
```
### Optional "pending", "source","balance"
_pending, source: version 9.0+_
_balance: version 12.0+_
Additionally checks if block is pending, returns source account for receive & open blocks (0 for send & change blocks), and returns the balance of the account at the time of the block.
Request:  
```
{  
  "action": "blocks_info",  
  "hashes": ["000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"],
  "pending": "true",
  "source": "true",
  "balance": "true"
}
```  
Response:  
```
{  
  "blocks" : {   
    "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F": {   
       "block_account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",   
       "amount": "1000000000000000000000000000000",   
       "contents": "{ ...skipped... }",
       "pending": "0",
       "source_account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
       "balance": "1000000000000000000000000000000"
     }
  }
}
```

## Block account  
Returns the account containing block  
Request:  
```
{  
  "action": "block_account",  
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}
```

## Block confirm   
_version 12.2+_   
Request confirmation for **block** from known online representative nodes. Check results with [Confirmation history](#confirmation-history)   
Request:  
```
{  
  "action": "block_confirm",  
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "started": "1"  
}
```

## Block count  
Reports the number of blocks in the ledger and unchecked synchronizing blocks   
Request:  
```
{  
  "action": "block_count"  
}
```  
Response:  
```
{
  "count": "1000",  
  "unchecked": "10"  
}
```

## Block count by type  
Reports the number of blocks in the ledger by type (send, receive, open, change)   
Request:  
```
{  
  "action": "block_count_type"  
}
```  
Response:  
```
{
    "send": "1000",   
    "receive": "900",   
    "open": "100",   
    "change": "50"  
}
```  

## Bootstrap  
Initialize bootstrap to specific **IP address** and **port**   
Request:  
```
{  
  "action": "bootstrap",  
  "address": "::ffff:138.201.94.249",  
  "port": "7075"  
}
```  
Response:  
```
{
  "success": ""  
}
```

## Multi-connection bootstrap  
Initialize multi-connection bootstrap to random peers   
Request:  
```
{  
  "action": "bootstrap_any"  
}
```  
Response:  
```
{
  "success": ""  
}
```

## Chain  
Returns a consecutive list of block hashes in the account chain starting at **block** up to **count**. Will list all blocks back to the open block of this chain when count is set to "-1". The requested block hash is included in the answer.  
Request:  
```
{  
  "action": "chain",
  "block": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "count": "1"    
}
```  
Response:  
```
{    
  "blocks" : [  
  "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
  ]  
}
```

## Confirmation history  
_version 12.0+_   
Returns hash & tally weight for recent elections winners   
Request:  
```
{  
  "action": "confirmation_history"      
}
```  
Response:  
```
{    
   "confirmations": [
        {
            "hash": "EA70B32C55C193345D625F766EEA2FCA52D3F2CCE0B3A30838CC543026BB0FEA",
            "tally": "80394786589602980996311817874549318248"
        },
        {
            "hash": "F2F8DA6D2CA0A4D78EB043A7A29E12BDE5B4CE7DE1B99A93A5210428EE5B8667",
            "tally": "68921714529890443063672782079965877749"
        }   
   ]
}
```   

## Delegators  
_version 8.0+_   
Returns a list of pairs of delegator names given **account** a representative and its balance  
Request:  
```
{  
  "action": "delegators",    
  "account": "xrb_1111111111111111111111111111111111111111111111111117353trpda"   
}
```  
Response:  
```
{    
   "delegators": {   
        "xrb_13bqhi1cdqq8yb9szneoc38qk899d58i5rcrgdk5mkdm86hekpoez3zxw5sd": "500000000000000000000000000000000000",   
        "xrb_17k6ug685154an8gri9whhe5kb5z1mf5w6y39gokc1657sh95fegm8ht1zpn": "961647970820730000000000000000000000"   
   }
}
```   

## Delegators count  
_version 8.0+_   
Get number of delegators for a specific representative **account**  
Request:  
```
{  
  "action": "delegators_count",    
  "account": "xrb_1111111111111111111111111111111111111111111111111117353trpda"   
}
```  
Response:  
```
{    
   "count": "2"   
}
```   

## Deterministic key  
Derive deterministic keypair from **seed** based on **index**  
Request:  
```
{  
  "action": "deterministic_key",
  "seed": "0000000000000000000000000000000000000000000000000000000000000000",  
  "index": "0"    
}
```  
Response:  
```
{  
  "private": "9F0E444C69F77A49BD0BE89DB92C38FE713E0963165CCA12FAF5712D7657120F",  
  "public": "C008B814A7D269A1FA3C6528B19201A24D797912DB9996FF02A1FF356E45552B",  
  "account": "xrb_3i1aq1cchnmbn9x5rsbap8b15akfh7wj7pwskuzi7ahz8oq6cobd99d4r3b7"  
}
```  

## Frontiers  
Returns a list of pairs of account and block hash representing the head block starting at **account** up to **count**  
Request:  
```
{  
  "action": "frontiers",
  "account": "xrb_1111111111111111111111111111111111111111111111111111hifc8npp",  
  "count": "1"    
}
```  
Response:  
```
{    
  "frontiers" : {  
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
  }  
}
```

## Frontier count  
Reports the number of accounts in the ledger  
Request:  
```
{  
  "action": "frontier_count"  
}
```  
Response:  
```
{
  "count": "1000"  
}
```

## History  

**Deprecated**: please use `account_history` instead. It provides a `head` option which is identical to the history `hash` option.

Request:  
```
{  
  "action": "history",  
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "count": "1"
}
```  
Response:  
```
{
    "history": [{
            "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
            "type": "receive",
            "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
            "amount": "100000000000000000000000000000000"
    }]
}
```

## Mrai from raw    
Divide a raw amount down by the Mrai ratio.  
Request:  
```
{  
  "action": "mrai_from_raw",  
  "amount": "1000000000000000000000000000000"
}
```  
Response:  
```
{  
  "amount": "1"  
}
```

## Mrai to raw    
Multiply an Mrai amount by the Mrai ratio.  
Request:  
```
{  
  "action": "mrai_to_raw",  
  "amount": "1"
}
```  
Response:  
```
{  
  "amount": "1000000000000000000000000000000"  
}
```

## Krai from raw    
Divide a raw amount down by the krai ratio.  
Request:  
```
{  
  "action": "krai_from_raw",  
  "amount": "1000000000000000000000000000"
}
```  
Response:  
```
{  
  "amount": "1"  
}
```

## Krai to raw    
Multiply an krai amount by the krai ratio.  
Request:  
```
{  
  "action": "krai_to_raw",  
  "amount": "1"
}
```  
Response:  
```
{  
  "amount": "1000000000000000000000000000"  
}
```

## Rai from raw    
Divide a raw amount down by the rai ratio.  
Request:  
```
{  
  "action": "rai_from_raw",  
  "amount": "1000000000000000000000000"
}
```  
Response:  
```
{  
  "amount": "1"  
}
```

## Rai to raw    
Multiply an rai amount by the rai ratio.  
Request:  
```
{  
  "action": "rai_to_raw",  
  "amount": "1"
}
```  
Response:  
```
{  
  "amount": "1000000000000000000000000"  
}
```

## Keepalive  
_enable_control required_  
Tells the node to send a keepalive packet to **address**:**port**  
Request:  
```
{  
  "action": "keepalive",
  "address": "::ffff:192.169.0.1",
  "port": "1024"  
}
```  
Response:  
```
{      
}
```

## Key create  
Generates an **adhoc random keypair**  
Request:  
```
{  
  "action": "key_create"  
}
```  
Response:  
```
{  
  "private": "781186FB9EF17DB6E3D1056550D9FAE5D5BBADA6A6BC370E4CBB938B1DC71DA3",  
  "public": "3068BB1CA04525BB0E416C485FE6A67FD52540227D267CC8B6E8DA958A7FA039",  
  "account": "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3sxwjym5rx"  
}
```  

## Key expand  
Derive public key and account number from **private key**  
Request:  
```
{  
  "action": "key_expand",  
  "key": "781186FB9EF17DB6E3D1056550D9FAE5D5BBADA6A6BC370E4CBB938B1DC71DA3"  
}
```  
Response:  
```
{  
  "private": "781186FB9EF17DB6E3D1056550D9FAE5D5BBADA6A6BC370E4CBB938B1DC71DA3",  
  "public": "3068BB1CA04525BB0E416C485FE6A67FD52540227D267CC8B6E8DA958A7FA039",  
  "account": "xrb_1e5aqegc1jb7qe964u4adzmcezyo6o146zb8hm6dft8tkp79za3sxwjym5rx"  
}
```  

## Ledger
_enable_control required, version 9.0+_   
Returns frontier, open block, change representative block, balance, last modified timestamp from local database & block count starting at **account** up to **count**   
Request:  
```
{  
  "action": "ledger",  
  "account": "xrb_1111111111111111111111111111111111111111111111111111hifc8npp",   
  "count": "1"    
}
```  
Response:  
```
{  
  "accounts": {   
    "xrb_11119gbh8hb4hj1duf7fdtfyf5s75okzxdgupgpgm1bj78ex3kgy7frt3s9n": {   
      "frontier": "E71AF3E9DD86BBD8B4620EFA63E065B34D358CFC091ACB4E103B965F95783321",   
      "open_block": "643B77F1ECEFBDBE1CC909872964C1DBBE23A6149BD3CEF2B50B76044659B60F",   
      "representative_block": "643B77F1ECEFBDBE1CC909872964C1DBBE23A6149BD3CEF2B50B76044659B60F",   
      "balance": "0",   
      "modified_timestamp": "1511476234",   
      "block_count": "2"   
    }   
  }   
}
```  
### Optional "representative", "weight", "pending"  
Additionally returns representative, voting weight, pending balance for each account   
Request:  
```
{  
  "action": "ledger",  
  "account": "xrb_1111111111111111111111111111111111111111111111111111hifc8npp",   
  "count": "1",   
  "representative": "true",  
  "weight": "true",  
  "pending": "true"  
}
```  
Response:  
```
{  
  "accounts": {   
    "xrb_11119gbh8hb4hj1duf7fdtfyf5s75okzxdgupgpgm1bj78ex3kgy7frt3s9n": {   
      "frontier": "E71AF3E9DD86BBD8B4620EFA63E065B34D358CFC091ACB4E103B965F95783321",  
      "open_block": "643B77F1ECEFBDBE1CC909872964C1DBBE23A6149BD3CEF2B50B76044659B60F",   
      "representative_block": "643B77F1ECEFBDBE1CC909872964C1DBBE23A6149BD3CEF2B50B76044659B60F",   
      "balance": "0",   
      "modified_timestamp": "1511476234",   
      "block_count": "2",   
      "representative": "xrb_1anrzcuwe64rwxzcco8dkhpyxpi8kd7zsjc1oeimpc3ppca4mrjtwnqposrs",   
      "weight": "0",   
      "pending": "0"   
    }   
  }   
}
```  
### Optional "modified_since"  
_version 11.0+_   
Return only accounts modified in local database after specific timestamp   

### Optional "sorting"  
Additional sorting accounts in descending order   

## Offline signing  (create block)
_enable_control required, version 9.0+_  
Creates a json representations of new block based on input data & signed with **private key** or **account** in *wallet**  
Request sample for **open block**:  
```
{  
  "action": "block_create",  
  "type": "open",  
  "key": "0000000000000000000000000000000000000000000000000000000000000001",   
  "account": "xrb_3kdbxitaj7f6mrir6miiwtw4muhcc58e6tn5st6rfaxsdnb7gr4roudwn951",   
  "representative": "xrb_1hza3f7wiiqa7ig3jczyxj5yo86yegcmqk3criaz838j91sxcckpfhbhhra1",   
  "source": "19D3D919475DEED4696B5D13018151D1AF88B2BD3BCFF048B45031C1F36D1858"   
}
```  
Parameters for **open block**:
* wallet (optional): The wallet ID that the account account the block is being created for is in.
* key (optional): Instead of using "wallet" parameter, you can directly pass in a private key.
* account: The account the block is being created for (xrb_youraccount)
* source: The block hash of the source of funds for this receive block (the send block that this receive block will pocket)
* representative: The account that the newly created account will use as its representative.

Response sample for **open block**:  
```
{  
  "hash": "F47B23107E5F34B2CE06F562B5C435DF72A533251CB414C51B2B62A8F63A00E4",
  "block": "{\n    \"type\": \"open\",\n    \"source\": \"19D3D919475DEED4696B5D13018151D1AF88B2BD3BCFF048B45031C1F36D1858\",\n    \"representative\": \"xrb_1hza3f7wiiqa7ig3jczyxj5yo86yegcmqk3criaz838j91sxcckpfhbhhra1\",\n    \"account\": \"xrb_3kdbxitaj7f6mrir6miiwtw4muhcc58e6tn5st6rfaxsdnb7gr4roudwn951\",\n    \"work\": \"4ec76c9bda2325ed\",\n    \"signature\": \"5974324F8CC42DA56F62FC212A17886BDCB18DE363D04DA84EEDC99CB4A33919D14A2CF9DE9D534FAA6D0B91D01F0622205D898293525E692586C84F2DCF9208\"\n}\n"   
}
```  
Request sample for **receive block**:  
```
{  
  "action": "block_create",  
  "type": "receive",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
  "account": "xrb_3kdbxitaj7f6mrir6miiwtw4muhcc58e6tn5st6rfaxsdnb7gr4roudwn951",   
  "source": "19D3D919475DEED4696B5D13018151D1AF88B2BD3BCFF048B45031C1F36D1858",   
  "previous": "F47B23107E5F34B2CE06F562B5C435DF72A533251CB414C51B2B62A8F63A00E4"
}
```  
Parameters for **receive block**:
* wallet (optional): The wallet ID that the account account the block is being created for is in.
* key (optional): Instead of using "wallet" parameter, you can directly pass in a private key.
* account: The account the block is being created for (xrb_youraccount)
* source: The block hash of the source of funds for this receive block (the send block that this receive block will pocket)
* previous: The block hash of the previous block on this account's block chain.

Response sample for **receive block**:  
```
{  
  "hash": "314BA8D9057678C1F53371C2DB3026C1FAC01EC8E7802FD9A2E8130FC523429E",
  "block": "{\n    \"type\": \"receive\",\n    \"previous\": \"F47B23107E5F34B2CE06F562B5C435DF72A533251CB414C51B2B62A8F63A00E4\",\n    \"source\": \"19D3D919475DEED4696B5D13018151D1AF88B2BD3BCFF048B45031C1F36D1858\",\n    \"work\": \"6acb5dd43a38d76a\",\n    \"signature\": \"A13FD22527771667D5DFF33D69787D734836A3561D8A490C1F4917A05D77EA09860461D5FBFC99246A4EAB5627F119AD477598E22EE021C4711FACF4F3C80D0E\"\n}\n"   
}
```  
Request sample for **send block**:  
```
{  
  "action": "block_create",  
  "type": "send",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
  "account": "xrb_3kdbxitaj7f6mrir6miiwtw4muhcc58e6tn5st6rfaxsdnb7gr4roudwn951",   
  "destination": "xrb_18gmu6engqhgtjnppqam181o5nfhj4sdtgyhy36dan3jr9spt84rzwmktafc",   
  "balance": "20000000000000000000000000000000",   
  "amount": "10000000000000000000000000000000",   
  "previous": "314BA8D9057678C1F53371C2DB3026C1FAC01EC8E7802FD9A2E8130FC523429E"  
}
```  
Parameters for **send block**:
* wallet (optional): The wallet ID that the account account the block is being created for is in.
* key (optional): Instead of using "wallet" parameter, you can directly pass in a private key.
* account: The account the block is being created for (xrb_youraccount)
* destination: The account that the sent funds should be accessible to
* balance: The **current balance** of the account that the send is originating from, formatted in 'raw' units using a decimal integer.
* amount: The amount being sent (must be less than or equal to balance), formatted in 'raw' units using a decimal integer.
* previous: The block hash of the previous block on this account's block chain.

**Warning:** It is **critical** that `balance` is the balance of the account at the `previous` block. If this is not the case, then the amount sent will be different than the `amount` parameter. This is because send blocks contain the balance after the send, so rai_node uses `balance - amount`. If balance is 1 Nano less than it should be, then 1 Nano more will be sent than should be.

Response sample for **send block**:  
```
{  
  "hash": "F958305C0FF0551421D4ABEDCCF302079D020A0A3833E33F185E2B0415D4567A",   
  "block": "{\n    \"type\": \"send\",\n    \"previous\": \"314BA8D9057678C1F53371C2DB3026C1FAC01EC8E7802FD9A2E8130FC523429E\",\n    \"destination\": \"xrb_18gmu6engqhgtjnppqam181o5nfhj4sdtgyhy36dan3jr9spt84rzwmktafc\",\n    \"balance\": \"0000007E37BE2022C0914B2680000000\",\n    \"work\": \"478563b2d9facfd4\",\n    \"signature\": \"F19CA177EFA8692C8CBF7478CE3213F56E4A85DF760DA7A9E69141849831F8FD79BA9ED89CEC807B690FB4AA42D5008F9DBA7115E63C935401F1F0EFA547BC00\"\n}\n"   
}
```  
In the response, the balance field contains the funds that will be left in the sending account afterwards (original balance minus amount sent), formatted in a 32 digit (128bit) zerofilled HEX number.  

Request sample for **change block**:  
```
{  
  "action": "block_create",  
  "type": "change",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
  "account": "xrb_3kdbxitaj7f6mrir6miiwtw4muhcc58e6tn5st6rfaxsdnb7gr4roudwn951",   
  "representative": "xrb_18gmu6engqhgtjnppqam181o5nfhj4sdtgyhy36dan3jr9spt84rzwmktafc",     
  "previous": "F958305C0FF0551421D4ABEDCCF302079D020A0A3833E33F185E2B0415D4567A"  
}
```  
Parameters for **change block**:
* wallet (optional): The wallet ID that the account account the block is being created for is in.
* key (optional): Instead of using "wallet" parameter, you can directly pass in a private key.
* account: The account the block is being created for (xrb_youraccount)
* representative: The account that the newly created account will use as its representative.
* previous: The block hash of the previous block on this account's block chain.

Response sample for **change block**:  
```
{  
  "hash": "654FA425CEBFC9E7726089E4EDE7A105462D93DBC915FFB70B50909920A7D286",  
  "block": "{\n    \"type\": \"change\",\n    \"previous\": \"F958305C0FF0551421D4ABEDCCF302079D020A0A3833E33F185E2B0415D4567A\",\n    \"representative\": \"xrb_18gmu6engqhgtjnppqam181o5nfhj4sdtgyhy36dan3jr9spt84rzwmktafc\",\n    \"work\": \"55e5b7a83edc3f4f\",\n    \"signature\": \"98B4D56881D9A88B170A6B2976AE21900C26A27F0E2C338D93FDED56183B73D19AA5BEB48E43FCBB8FF8293FDD368CEF50600FECEFD490A0855ED702ED209E04\"\n}\n"  
}
```  
### Optional "work"  
Uses **work** value for block from external source  

## Payment begin
Begin a new payment session. Searches wallet for an account that's marked as available and has a 0 balance. If one is found, the account number is returned and is marked as unavailable. If no account is found, a new account is created, placed in the wallet, and returned.  
Request:  
```
{  
"action": "payment_begin",  
"wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
"account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}
```  

## Payment init  
Marks all accounts in wallet as available for being used as a payment session.  
Request:  
```
{  
  "action": "payment_init",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "status" : "Ready"  
}
```  

## Payment end  
End a payment session.  Marks the account as available for use in a payment session. 
Request:  
```
{  
  "action": "payment_end",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "wallet": "FFFD1BAEC8EC20814BBB9059B393051AAA8380F9B5A2E6B2489A277D81789EEE"  
}
```  
Response:  
```
{}
```   

## Payment wait  
Wait for payment of 'amount' to arrive in 'account' or until 'timeout' milliseconds have elapsed.  
Request:  
```
{  
  "action": "payment_wait",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "amount": "1",  
  "timeout": "1000"  
}
```  
Response:  
```
{  
  "status" : "success"  
}
```  

## Process block  
Publish **block** to the network  
Request:  
```
{  
  "action": "process",  
  "block": "{
    \"type\": \"open\",
    \"account\": \"xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000\",
    \"representative\": \"xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000\",
    \"source\": \"FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4\",
    \"work\": \"0000000000000000\",
    \"signature\": \"00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000\"
}"  
}
```  
Response:  
```
{  
  "hash": "42A723D2B60462BF7C9A003FE9A70057D3A6355CA5F1D0A57581000000000000"   
}
```


## Receive  
_enable_control required_  
Receive pending **block** for **account** in **wallet**  
Request:  
```
{  
  "action": "receive",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "block": "53EAA25CE28FA0E6D55EA9704B32604A736966255948594D55CBB05267CECD48"  
}
```  
Response:  
```
{  
  "block": "EE5286AB32F580AB65FD84A69E107C69FBEB571DEC4D99297E19E3FA5529547B"  
}
```
### Optional "work"  
_version 9.0+_  
Uses **work** value for block from external source  

## Receive minimum  
_enable_control required, version 8.0+_   
Returns receive minimum for node  
Request:  
```
{  
  "action": "receive_minimum"  
}
```  
Response:  
```
{  
  "amount": "1000000000000000000000000"  
}
```

## Receive minimum set  
_enable_control required, version 8.0+_   
Set **amount** as new receive minimum for node until restart  
Request:  
```
{  
  "action": "receive_minimum_set",  
  "amount": "1000000000000000000000000000000"
}
```  
Response:  
```
{  
  "success": ""  
}
```

## Representatives  
Returns a list of pairs of representative and its voting weight  
Request:  
```
{  
  "action": "representatives"    
}
```  
Response:  
```
{    
  "representatives" : {  
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": "3822372327060170000000000000000000000",  
    "xrb_1111111111111111111111111111111111111111111111111awsq94gtecn": "30999999999999999999999999000000",  
    "xrb_114nk4rwjctu6n6tr6g6ps61g1w3hdpjxfas4xj1tq6i8jyomc5d858xr1xi": "0"  
  }  
}
```
### Optional "count"  
_version 9.0+_   
Returns a list of pairs of representative and its voting weight up to **count**    
### Optional "sorting"  
_version 9.0+_   
Additional sorting represetntatives in descending order     


## Representatives online  
_version 11.2+_   
Returns a list of pairs of online representative accounts that have voted recently and empty strings  
Request:  
```
{  
  "action": "representatives_online"    
}
```  
Response:  
```
{    
  "representatives" : {  
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": "",  
    "xrb_1111111111111111111111111111111111111111111111111awsq94gtecn": "",  
    "xrb_114nk4rwjctu6n6tr6g6ps61g1w3hdpjxfas4xj1tq6i8jyomc5d858xr1xi": ""  
  }  
}
```

## Wallet representative  
Returns the default representative for **wallet**  
Request:  
```
{  
  "action": "wallet_representative",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
}
```  
Response:  
```
{  
  "representative" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"
}
```

## Wallet representative set  
_enable_control required_  
Sets the default **representative** for **wallet**  
Request:  
```
{  
  "action": "wallet_representative_set",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"
}
```  
Response:  
```
{  
  "set": "1"
}
```


## Republish  
Rebroadcast blocks starting at **hash** to the network    
Request:  
```
{  
  "action": "republish",    
  "hash": "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948"    
}
```  
Response:  
```
{    
  "blocks": [   
     "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
     "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293"
  ]       
}
```   
### Optional "sources"  
_version 8.0+_   
Additionally rebroadcast source chain blocks for receive/open up to **sources** depth   
Request:  
```
{  
  "action": "republish",    
  "hash": "90D0C16AC92DD35814E84BFBCC739A039615D0A42A76EF44ADAEF1D99E9F8A35",    
  "count": "1",    
  "sources": "2"   
}
```  
Response:  
```
{    
  "blocks": [   
      "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
      "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293",   
      "90D0C16AC92DD35814E84BFBCC739A039615D0A42A76EF44ADAEF1D99E9F8A35"   
  ]       
}
```   

### Optional "destinations"  
_version 8.0+_   
Additionally rebroadcast destination chain blocks from receive up to **destinations** depth   
Request:  
```
{  
  "action": "republish",    
  "hash": "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293",    
  "count": "1",    
  "destinations": "2"   
}
```  
Response:  
```
{    
  "blocks": [   
      "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293",   
      "90D0C16AC92DD35814E84BFBCC739A039615D0A42A76EF44ADAEF1D99E9F8A35",   
      "18563C814A54535B7C12BF76A0E23291BA3769536634AB90AD0305776A533E8E"   
  ]       
}
```   


## Search pending  
_enable_control required_  
Tells the node to look for pending blocks for any account in **wallet**  
Request:  
```
{  
  "action": "search_pending",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
}
```  
Response:  
```
{
  "started": "1"  
}
```


## Search pending for all wallets  
_enable_control required, version 8.0+_  
Tells the node to look for pending blocks for any account in all available wallets  
Request:  
```
{  
  "action": "search_pending_all"
}
```  
Response:  
```
{
  "success": ""  
}
```

## Send  
_enable_control required_  
Send **amount** from **source** in **wallet** to **destination**  
Request:  
```
{  
  "action": "send",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "source": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "destination": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
  "amount": "1000000"  
}
```  
Response:  
```
{  
  "block": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```
Proof of Work is precomputed for **one** transaction in the background.  If it has been a while since your last transaction it will send instantly, the next one will need to wait for Proof of Work to be generated.

If the request times out, then the send may or may not have gone through. Most exchange "double withdraw" bugs are caused because a request was incorrectly retried. If you want to the ability to retry a failed send, all send calls must specify the id parameter as follows

### Highly recommended "id"
_version 10.0+_  

You can (and should) specify a **unique** id for each spend to provide [idempotency](https://en.wikipedia.org/wiki/Idempotence#Computer_science_meaning). That means that if you call `send` two times with the same id, the second request won't send any additional Nano, and will return the first block instead. The id can be any string. **This may be a required parameter in the future.**

If you accidentally reuse an id, the send will not go through (it will be seen as a duplicate request), so make sure your ids are unique! They must be unique per node, and are not segregated per wallet.

Using the same id for requests with different parameters (wallet, source, destination, and amount) is undefined behavior and may result in an error in the future.

Request:  
```
{  
  "action": "send",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "source": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "destination": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
  "amount": "1000000",
  "id": "7081e2b8fec9146e"
}
```  
Response:  
```
{  
  "block": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```

Sending the request again will yield the same block, and will not affect the ledger.

In the future, the response may also indicate if the block is new. However, that has not yet been implemented.

### Optional "work"  
_version 9.0+_  
Uses **work** value for block from external source  
Request:  
```
{  
  "action": "send",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "source": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",  
  "destination": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
  "amount": "1000000",   
  "work": "2bf29ef00786a6bc"   
}
```  

## Statistics
_version 12.2+_  
For configuration and other details, please see [Statistics](https://github.com/nanocurrency/raiblocks/wiki/Statistics)

Request counters:
```
{
    "action": "stats",
    "type": "counters"
}
```

Counters response:
```
{
    "type": "counters",
    "created": "2018.03.29 01:46:36",
    "entries": [
        {
            "time": "01:46:36",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "3122792"
        },
        {
            "time": "01:46:36",
            "type": "traffic",
            "detail": "all",
            "dir": "out",
            "value": "203184"
        } 
        ...
    ]
}
```

Request samples:
```
{
    "action": "stats",
    "type": "samples"
}
```

Samples response:
```
{
    "type": "samples",
    "created": "2018.03.29 01:47:08",
    "entries": [
        {
            "time": "01:47:04",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "59480"
        },
        {
            "time": "01:47:05",
            "type": "traffic",
            "detail": "all",
            "dir": "in",
            "value": "44496"
        }
        ...
     ]
}
```

## Stop node   
_enable_control required_  
Method to safely shutdown node  
Request:  
```
{  
  "action": "stop"  
}
```  
Response:  
```
{  
  "success": ""  
}
```  

## Validate account number checksum  
Check whether **account** is a valid account number  
Request:  
```
{  
  "action": "validate_account_number",  
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"  
}
```  
Response:  
```
{  
  "valid" : "1"
}
```


## Successors  
Returns a list of block hashes in the account chain ending at **block** up to **count**  
Request:  
```
{  
  "action": "successors",
  "block": "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",  
  "count": "1"    
}
```  
Response:  
```
{    
  "blocks" : [  
  "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293"  
  ]  
}
```

## Retrieve node versions 
Returns version information for RPC, Store & Node (Major & Minor version)  
_RPC Version always retruns "1" as of 13/01/2018_  
Request:  
```
{  
  "action": "version" 
}
```  
Response:  
```
{  
  "rpc_version" : "1",
  "store_version" : "2",
  "node_vendor" : "RaiBlocks 7.5.0"
}
```

## Retrieve online peers  
Returns a list of pairs of peer IPv6:port and its node network version    
Request:  
```
{  
  "action": "peers" 
}
```  
_version 8.0+_   
Response:  
```
{
    "peers": {  
        "[::ffff:172.17.0.1]:32841": "3"  
    }  
}
```   
Response before 8.0+:  
```
{
    "peers": [  
        "[::ffff:172.17.0.1]:32841"  
    ]  
}
```   

## Pending  
Returns a list of block hashes which have not yet been received by this account.  
```
{  
  "action": "pending",
  "account": "xrb_1111111111111111111111111111111111111111111111111117353trpda",  
  "count": "1"    
}
```  
Response:  
```
{    
  "blocks" : [ "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F" ]  
}
```   
### Optional "threshold"  
_version 8.0+_   
Returns a list of pending block hashes with amount more or equal to **threshold**  
Request:  
```
{  
  "action": "pending",  
  "account": "xrb_1111111111111111111111111111111111111111111111111117353trpda",  
  "count": "1",  
  "threshold": "1000000000000000000000000"   
}
```  
Response:  
```
{  
  "blocks" : {    
        "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F": "6000000000000000000000000000000"    
    }  
}
```  
### Optional "source"  
_version 9.0+_   
Returns a list of pending block hashes with amount and source accounts   
Request:  
```
{  
  "action": "pending",  
  "account": "xrb_1111111111111111111111111111111111111111111111111117353trpda",  
  "count": "1",  
  "source": "true"   
}
```  
Response:  
```
{  
  "blocks" : {    
        "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F": {   
             "amount": "6000000000000000000000000000000",       
             "source": "xrb_3dcfozsmekr1tr9skf1oa5wbgmxt81qepfdnt7zicq5x3hk65fg4fqj58mbr"  
        }   
    }  
}
```  

## Pending exists  
_version 8.0+_   
Check whether block is pending by **hash**  
Request:  
```
{  
  "action": "pending_exists",
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F" 
}
```  
Response:  
```
{  
  "exists" : "1"
}
```

## Unchecked blocks  
_version 8.0+_   
Returns a list of pairs of unchecked synchronizing block hash and its json representation up to **count**          
Request:  
```
{  
  "action": "unchecked",
  "count": "1" 
}
```  
Response:  
```
{  
    "blocks": {  
       "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F": "{
          "type": "open",
          "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
          "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
          "source": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",
          "work": "0000000000000000",
          "signature": 
 "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
       }"
    }
}
```

## Clear unchecked blocks   
_enable_control required, version 8.0+_     
Clear unchecked synchronizing blocks   
Request:  
```
{  
    "action": "unchecked_clear"   
}
```  
Response:  
```
{  
    "success": ""  
}
```  

## Retrieve unchecked block  
_version 8.0+_  
Retrieves a json representation of unchecked synchronizing block by **hash**     
Request:  
```
{  
  "action": "unchecked_get",  
  "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "contents" : "{
    "type": "open",
    "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
    "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
    "source": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",
    "work": "0000000000000000",
    "signature": "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
}"
}
```

## Unchecked blocks with database keys   
_version 8.0+_   
Retrieves unchecked database keys, blocks hashes & a json representations of unchecked pending blocks starting from **key** up to **count**   
Request:  
```
{  
  "action": "unchecked_keys",
  "key": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",   
  "count": "1" 
}
```  
Response:  
```
{  
    "unchecked": [
       { 
          "key": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",   
          "hash": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
          "contents": "{
             "type": "open",
             "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
             "representative": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
             "source": "FA5B51D063BADDF345EFD7EF0D3C5FB115C85B1EF4CDE89D8B7DF3EAF60A04A4",
             "work": "0000000000000000",
             "signature": 
 "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
          }"   
       }   
    ]   
}
```   

## Wallet add key  
_enable_control required_  
Add an adhoc private key **key** to **wallet**  
Request:  
```
{  
  "action": "wallet_add",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "key": "34F0A37AAD20F4A260F0A5B3CB3D7FB50673212263E58A380BC10474BB039CE4"  
}
```  
Response:  
```
{  
  "account" : "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000"
}
```
### Optional disabling work generation  
_version 9.0+_  
Disables work generation after adding account  
Request:  
```
{  
  "action": "wallet_add",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "key": "34F0A37AAD20F4A260F0A5B3CB3D7FB50673212263E58A380BC10474BB039CE4",  
  "work": "false"  
}
```  

## Wallet add watch-only accounts  
_enable_control required, version 11.0+_  
Add watch-only **accounts** to **wallet**  
Request:  
```
{  
  "action": "wallet_add_watch",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "accounts": [
    "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000",
    "xrb_111111111111111111111111111111111111111111111111111000000000"
  ]  
}
```  
Response:  
```
{  
  "success" : ""
}
```

## Wallet total balance  
Returns the sum of all accounts balances in **wallet**  
Request:  
```
{  
  "action": "wallet_balance_total",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "balance": "10000",  
  "pending": "10000"  
}
```

## Wallet accounts balances  
Returns how many rai is owned and how many have not yet been received by all accounts in **wallet**  
Request:  
```
{  
  "action": "wallet_balances",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "balances" : {  
    "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000": {  
      "balance": "10000",  
      "pending": "10000"  
    }
  }   
}
```
### Optional "threshold"  
_version 9.0+_   
Returns wallet accounts balances more or equal to **threshold**   

## Wallet change seed  
_enable_control required_  
Changes seed for **wallet** to **seed**.  ***Notes:*** Clear all deterministic accounts in wallet! To restore account from new seed use RPC [Accounts create](#accounts-create)  
Request:  
```
{  
  "action": "wallet_change_seed",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "seed": "74F2B37AAD20F4A260F0A5B3CB3D7FB51673212263E58A380BC10474BB039CEE"  
}
```  
Response:  
```
{  
  "success" : ""
}
```

## Wallet contains  
Check whether **wallet** contains **account**  
Request:  
```
{  
  "action": "wallet_contains",
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "account": "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000" 
}
```  
Response:  
```
{  
  "exists" : "1"
}
```

## Wallet create  
_enable_control required_  
Creates a new random wallet id  
Request:  
```
{  
  "action": "wallet_create" 
}
```  
Response:  
```
{  
  "wallet" : "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"
}
```

## Wallet destroy  
_enable_control required_  
Destroys **wallet** and all contained accounts  
Request:  
```
{  
  "action": "wallet_destroy",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
}
```

## Wallet export  
Return a json representation of **wallet**  
Request:  
```
{  
  "action": "wallet_export",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"   
}
```  
Response:  
```
{  
  "json" : "{\"0000000000000000000000000000000000000000000000000000000000000000\": \"0000000000000000000000000000000000000000000000000000000000000001\"}"
}
```

## Wallet frontiers  
Returns a list of pairs of account and block hash representing the head block starting for accounts from **wallet**  
Request:  
```
{  
  "action": "wallet_frontiers",
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"    
}
```  
Response:  
```
{    
  "frontiers" : {  
  "xrb_3e3j5tkog48pnny9dmfzj1r16pg8t1e76dz5tmac6iq689wyjfpi00000000": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
  }  
}
```

## Wallet ledger
_enable_control required, version 11.0+_   
Returns frontier, open block, change representative block, balance, last modified timestamp from local database & block count for accounts from **wallet**   
Request:  
```
{  
  "action": "wallet_ledger",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"   
}
```  
Response:  
```
{  
  "accounts": {   
    "xrb_11119gbh8hb4hj1duf7fdtfyf5s75okzxdgupgpgm1bj78ex3kgy7frt3s9n": {   
      "frontier": "E71AF3E9DD86BBD8B4620EFA63E065B34D358CFC091ACB4E103B965F95783321",   
      "open_block": "643B77F1ECEFBDBE1CC909872964C1DBBE23A6149BD3CEF2B50B76044659B60F",   
      "representative_block": "643B77F1ECEFBDBE1CC909872964C1DBBE23A6149BD3CEF2B50B76044659B60F",   
      "balance": "0",   
      "modified_timestamp": "1511476234",   
      "block_count": "2"   
    }   
  }   
}
```  
### Optional "representative", "weight", "pending"  
Additionally returns representative, voting weight, pending balance for each account   
Request:  
```
{  
  "action": "wallet_ledger",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
  "representative": "true",  
  "weight": "true",  
  "pending": "true"  
}
```  
Response:  
```
{  
  "accounts": {   
    "xrb_11119gbh8hb4hj1duf7fdtfyf5s75okzxdgupgpgm1bj78ex3kgy7frt3s9n": {   
      "frontier": "E71AF3E9DD86BBD8B4620EFA63E065B34D358CFC091ACB4E103B965F95783321",  
      "open_block": "643B77F1ECEFBDBE1CC909872964C1DBBE23A6149BD3CEF2B50B76044659B60F",   
      "representative_block": "643B77F1ECEFBDBE1CC909872964C1DBBE23A6149BD3CEF2B50B76044659B60F",   
      "balance": "0",   
      "modified_timestamp": "1511476234",   
      "block_count": "2",   
      "representative": "xrb_1anrzcuwe64rwxzcco8dkhpyxpi8kd7zsjc1oeimpc3ppca4mrjtwnqposrs",   
      "weight": "0",   
      "pending": "0"   
    }   
  }   
}
```  
### Optional "modified_since"  
Return only accounts modified in local database after specific timestamp   

## Wallet pending  
_enable_control required, version 8.0+_   
Returns a list of block hashes which have not yet been received by accounts in this **wallet**  
Request:  
```
{  
  "action": "wallet_pending",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"    
  "count": "1"
}
```  
Response:  
```
{  
  "blocks" : {  
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": ["142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D"],  
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": ["4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74"]  
  }  
}
```  
### Optional "threshold"  
Returns a list of pending block hashes with amount more or equal to **threshold**   
Request:  
```
{  
  "action": "wallet_pending",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",    
  "count": "1",  
  "threshold": "1000000000000000000000000"   
}
```  
Response:  
```
{  
  "blocks" : {
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": {    
        "142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D": "6000000000000000000000000000000"    
    },    
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": {    
        "4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74": "106370018000000000000000000000000"    
    }  
}
```  
### Optional "source"  
_version 9.0+_   
Returns a list of pending block hashes with amount and source accounts   
Request:  
```
{  
  "action": "wallet_pending",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",    
  "count": "1",  
  "source": "true"   
}
```  
Response:  
```
{  
  "blocks" : {
    "xrb_1111111111111111111111111111111111111111111111111117353trpda": {    
        "142A538F36833D1CC78B94E11C766F75818F8B940771335C6C1B8AB880C5BB1D": {   
             "amount": "6000000000000000000000000000000",       
             "source": "xrb_3dcfozsmekr1tr9skf1oa5wbgmxt81qepfdnt7zicq5x3hk65fg4fqj58mbr"
        }
    },    
    "xrb_3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3": {    
        "4C1FEEF0BEA7F50BE35489A1233FE002B212DEA554B55B1B470D78BD8F210C74": {   
             "amount": "106370018000000000000000000000000",       
             "source": "xrb_13ezf4od79h1tgj9aiu4djzcmmguendtjfuhwfukhuucboua8cpoihmh8byo"
        }   
    }  
}
```  

## Wallet republish  
_enable_control required, version 8.0+_   
Rebroadcast blocks for accounts from **wallet** starting at frontier down to **count** to the network     
Request:  
```
{  
  "action": "wallet_republish",    
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",
  "count": "2"   
}
```  
Response:  
```
{    
  "blocks": [   
      "991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948",   
      "A170D51B94E00371ACE76E35AC81DC9405D5D04D4CEBC399AEACE07AE05DD293",   
      "90D0C16AC92DD35814E84BFBCC739A039615D0A42A76EF44ADAEF1D99E9F8A35"   
  ]       
}
```   


## Wallet work get
_enable_control required, version 8.0+_     
Returns a list of pairs of account and work from **wallet**   
Request:  
```
{  
    "action": "wallet_work_get",  
    "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
   "works": {
       "xrb_1111111111111111111111111111111111111111111111111111hifc8npp": "432e5cf728c90f4f"   
   }
}
```  

## Wallet change password  
_enable_control required_  
Changes the password for **wallet** to **password**  
Request:  
```
{  
  "action": "password_change",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "password": "test"  
}
```  
Response:  
```
{  
  "changed" : "1"
}
```

## Wallet password enter (unlock wallet)  
Enters the **password** in to **wallet**  
Request:  
```
{  
  "action": "password_enter",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
  "password": "test"  
}
```  
Response:  
```
{  
  "valid" : "1"
}
```

## Wallet valid password  
Checks whether the password entered for **wallet** is valid  
Request:  
```
{  
  "action": "password_valid",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "valid" : "1"
}
```

## Wallet lock   
_enable_control required, version 9.0+_  
Locks **wallet**  
Request:  
```
{  
  "action": "wallet_lock",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "locked" : "1"
}
```

## Wallet locked check   
Checks whether **wallet** is locked  
Request:  
```
{  
  "action": "wallet_locked",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F"  
}
```  
Response:  
```
{  
  "locked" : "0"
}
```

## Work cancel
_enable_control required_  
Stop generating **work** for block  
Request:  
```
{  
    "action": "work_cancel",  
    "hash": "718CC2121C3E641059BC1C2CFC45666C99E8AE922F7A807B7D07B62C995D79E2"  
}
```  
Response:  
```
{  
}
```  

## Work generate
_enable_control required_  
Generates **work** for block  
Request:  
```
{  
    "action": "work_generate",  
    "hash": "718CC2121C3E641059BC1C2CFC45666C99E8AE922F7A807B7D07B62C995D79E2"  
}
```  
Response:  
```
{  
    "work": "2bf29ef00786a6bc"  
}
```  

## Work get
_enable_control required, version 8.0+_     
Retrieves work for **account** in **wallet**  
Request:  
```
{  
    "action": "work_get",  
    "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
    "account": "xrb_1111111111111111111111111111111111111111111111111111hifc8npp"  
}
```  
Response:  
```
{  
    "work": "432e5cf728c90f4f"  
}
```  

## Work set
_enable_control required, version 8.0+_     
Set **work** for **account** in **wallet**  
Request:  
```
{  
    "action": "work_set",  
    "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",   
    "account": "xrb_1111111111111111111111111111111111111111111111111111hifc8npp",  
    "work": "0000000000000000"  
}
```  
Response:  
```
{  
    "success": ""  
}
```  

## Add work peer  
_enable_control required, version 8.0+_     
Add specific **IP address** and **port** as work peer for node until restart   
Request:  
```
{  
    "action": "work_peer_add",  
    "address": "::ffff:172.17.0.1:7076",  
    "port": "7076" 
}
```  
Response:  
```
{  
    "success": ""  
}
```  

## Retrieve work peers   
_enable_control required, version 8.0+_     
Request:  
```
{  
    "action": "work_peers"   
}
```  
Response:  
```
{  
    "work_peers": [   
        "::ffff:172.17.0.1:7076"   
    ]   
}
```  

## Clear work peers  
_enable_control required, version 8.0+_     
Clear work peers node list until restart   
Request:  
```
{  
    "action": "work_peers_clear"   
}
```  
Response:  
```
{  
    "success": ""  
}
```  

## Work validate 
Check whether **work** is valid for block  
Request:  
```
{  
    "action": "work_validate",  
    "work": "2bf29ef00786a6bc",  
    "hash": "718CC2121C3E641059BC1C2CFC45666C99E8AE922F7A807B7D07B62C995D79E2"  
}
```  
Response:  
```
{  
    "valid": "1"  
}
```  

## RPC callback
Send JSON POST requests with every new block to callback server _http://callback_address:callback_port<callback_target>_ defined in [config.json](https://github.com/clemahieu/raiblocks/wiki/config.json). Callback target should include a leading slash. Block object is returned as a string [issue/749](https://github.com/nanocurrency/raiblocks/issues/749) 
Sample:  
https://localhost:8080/callback  

```
{  
    "account": "xrb_1m5cfk468k9cwfdp8zsiktc3dghxh6qabef7mno5odos9h91nn5wzs58g7st",  
    "hash": "B5678177F615A890C28F6716FBD81E1068ADAC27C85E00EDCCC21832CFF1C413",  
    "block": {  
        "type": "send",  
        "previous": "F91264792342F6B99CC9B3C946726537EFA5F7C925CCCAB49C32B5B423CCB07B",  
        "destination": "xrb_39ymww61tksoddjh1e43mprw5r8uu1318it9z3agm7e6f96kg4ndqg9tuds4",  
        "balance": "000000015D47BE1FF551BFBBE1000000",  
        "work": "f57ec8eab4e3d760",  
        "signature": "DBD8ECA13CCDEC87FAE0E7B2AAA2460492249410A18E9C06AD454862260038D8B55ACD130F9C402C24ED3E97C579E33C82B93368156B8E0E4183CF7B45205B0A"  
    },  
    "amount": "1099000000000000000000000000000000"  
}
```  

Note: You should fetch the block using the hash provided in the callback rather than trust this data is valid, and check that data instead, since a malicious 3rd party can also make a fake callback request to your endpoint.