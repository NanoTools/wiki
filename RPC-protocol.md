The RPC protocol accepts JSON http requests.  The following are RPC commands along with the responses that are expected.

## Send  
Request:  
`{  
  "action": "send",  
  "account": "U63Kt2zHcikQvirWSSNKZHbfVZsPY68A65zyD1NtQoE5HsWZTf",
  "amount": "1000000"  
}`  
Response:  
`{  
  "sent": "1"  
}`

## Account balance  
Request:  
`{  
  "action": "account_balance",  
  "account": "U63Kt2zHcikQvirWSSNKZHbfVZsPY68A65zyD1NtQoE5HsWZTf"  
}`  
Response:  
`{  
  "balance": "0"  
}`

## Account create  
Request:  
`{  
  "action": "wallet_create",  
}`  
Response:  
`{  
  "account" : "U63Kt2zHcikQvirWSSNKZHbfVZsPY68A65zyD1NtQoE5HsWZTf"  
}`

## Wallet contains  
Request:  
`{  
  "action": "wallet_contains",  
  "account": "U63Kt2zHcikQvirWSSNKZHbfVZsPY68A65zyD1NtQoE5HsWZTf"  
}`  
Response:  
`{  
  "exists" : "1"
}`

## Validate account number checksum  
Request:  
`{  
  "action": "validate_account",  
  "account": "U63Kt2zHcikQvirWSSNKZHbfVZsPY68A65zyD1NtQoE5HsWZTf"  
}`  
Response:  
`{  
  "valid" : "1"
}`