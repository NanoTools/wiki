The RPC protocol accepts JSON http requests.  The following are RPC commands along with the responses that are expected.

## Send  
Request:  
`{  
  "action": "send",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8",
  "amount": "1000000"  
}`  
Response:  
`{  
  "sent": "1"  
}`

## Send exact  
Request:  
`{  
  "action": "send_exact",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8",
  "amount": "100000000000000000000000000"  
}`  
Response:  
`{  
  "sent": "1"  
}`

## Account balance  
Request:  
`{  
  "action": "account_balance",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`  
Response:  
`{  
  "balance": "10000"  
}`

## Account balance exact  
Request:  
`{  
  "action": "account_balance_exact",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`  
Response:  
`{  
  "balance": "1000000000000000000000000"  
}`

## Account weight  
Request:  
`{  
  "action": "account_weight",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`  
Response:  
`{  
  "weight": "10000"  
}`

## Account weight exact  
Request:  
`{  
  "action": "account_weight_exact",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`  
Response:  
`{  
  "weight": "1000000000000000000000000"  
}`

## Account create  
Request:  
`{  
  "action": "wallet_create",  
}`  
Response:  
`{  
  "account" : "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`

## Wallet valid password 
Request:  
`{  
  "action": "password_valid"
}`  
Response:  
`{  
  "valid" : "1"
}`

## Wallet change password  
Request:  
`{  
  "action": "password_change",  
  "password": "test"  
}`  
Response:  
`{  
  "changed" : "1"
}`

## Wallet password enter  
Request:  
`{  
  "action": "password_enter",  
  "password": "test"  
}`  
Response:  
`{  
  "valid" : "1"
}`

## Wallet contains  
Request:  
`{  
  "action": "wallet_contains",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`  
Response:  
`{  
  "exists" : "1"
}`

## Wallet list  
Request:  
`{  
  "action": "wallet_list"  
}`  
Response:  
`{  
  "accounts" : [
  "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
  ]
}`

## Wallet add  
Request:  
`{  
  "action": "wallet_add",  
  "key": "34F0A37AAD20F4A260F0A5B3CB3D7FB50673212263E58A380BC10474BB039CE4"  
}`  
Response:  
`{  
  "account" : "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"
}`

## Wallet key valid  
Request:  
`{  
  "action": "wallet_key_valid"  
}`  
Response:  
`{  
  "valid" : "1"
}`

## Validate account number checksum  
Request:  
`{  
  "action": "validate_account",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`  
Response:  
`{  
  "valid" : "1"
}`