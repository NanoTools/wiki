The RPC protocol accepts JSON http requests.  The following are RPC commands along with the responses that are expected.

## Send  
Request:  
`{  
  "action": "send",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
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
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
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
  "action": "account_create",  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
}`  
Response:  
`{  
  "account" : "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`

## Account list  
Request:  
`{  
  "action": "account_list"  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
}`  
Response:  
`{  
  "accounts" : [
  "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
  ]
}`

## Wallet valid password 
Request:  
`{  
  "action": "password_valid"  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
}`  
Response:  
`{  
  "valid" : "1"
}`

## Wallet change password  
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

## Wallet contains  
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

## Wallet add  
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

## Wallet key valid  
Request:  
`{  
  "action": "wallet_key_valid"  
  "wallet": "000D1BAEC8EC208142C99059B393051BAC8380F9B5A2E6B2489A277D81789F3F",  
}`  
Response:  
`{  
  "valid" : "1"
}`

## Validate account number checksum  
Request:  
`{  
  "action": "validate_account_number",  
  "account": "U63Kt3B7yp2iQB4GsVWriGv34kk2qwhT7acKvn8yWZGdNVesJ8"  
}`  
Response:  
`{  
  "valid" : "1"
}`