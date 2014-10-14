The RPC protocol accepts JSON http requests.  The following are RPC commands along with the responses that are expected.

### Account balance request:
`{
  "action": "account_balance",
  "account": "0"
}`

### Account balance response:
`{
  "balance": "0"
}`


### Account create request:
`{
  "action": "wallet_create",
}`

### Account create response:
`{
  "account" : "42F1B65476C8AFB1FA3CD145EB0772077A454562B318FD64ED81C435303A2E76"
}`