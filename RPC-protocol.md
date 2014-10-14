The RPC protocol accepts JSON http requests.  The following are RPC commands along with the responses that are expected.

## Account balance request:
`{
  "action": "account_balance",
  "account": "42F1B65476C8AFB1FA3CD145EB0772077A454562B318FD64ED81C435303A2E76"
}`

### Response:
`{
  "balance": "0"
}`


### Account create request:
`{
  "action": "wallet_create",
}`

## Response:
`{
  "account" : "42F1B65476C8AFB1FA3CD145EB0772077A454562B318FD64ED81C435303A2E76"
}`

## Wallet contains request:
`{
  "action": "wallet_contains",
  "account": "42F1B65476C8AFB1FA3CD145EB0772077A454562B318FD64ED81C435303A2E76"
}`

### Response:
`{
  "exists" : "1"
}`
