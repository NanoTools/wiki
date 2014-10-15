The RPC protocol accepts JSON http requests.  The following are RPC commands along with the responses that are expected.

## Account balance request:  
`{
  "action": "account_balance",
  "account": "U63Kt2zHcikQvirWSSNKZHbfVZsPY68A65zyD1NtQoE5HsWZTf"
}`  
Response:  
`{
  "balance": "0"
}`

## Account create request:
`{
  "action": "wallet_create",
}`  
Response:  
`{
  "account" : "U63Kt2zHcikQvirWSSNKZHbfVZsPY68A65zyD1NtQoE5HsWZTf"
}`

## Wallet contains request:
`{
  "action": "wallet_contains",
  "account": "U63Kt2zHcikQvirWSSNKZHbfVZsPY68A65zyD1NtQoE5HsWZTf"
}`  
Response:  
`{
  "exists" : "1"
}`
