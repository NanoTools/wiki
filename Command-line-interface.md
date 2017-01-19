
### --account_create --wallet=`<wallet>`
Insert next deterministic key in to `<wallet>`

### --account_get --key=`<key>`
Get account number for the `<key>`

### --account_key --account=`<account>`
Get the public key for `<account>`

### --diagnostics
Run internal diagnostics

### --key_create
Generates a adhoc random keypair and prints it to stdout

### --key_expand --key=`<key>`
Derive public key and account number from `<key>`

### --wallet_add_adhoc --wallet=`<wallet>` --key=`<key>`
Insert `<key>` in to `<wallet>`

### --wallet_create
Creates a new wallet and prints the ID

### --wallet_change_seed --wallet=`<wallet>` --key=`<key>`
Changes seed for `<wallet>` to `<key>`

### --wallet_decrypt_unsafe --wallet=`<wallet>` --password=`<password>`
Decrypts `<wallet>` using `<password>`  
**!!THIS WILL PRINT YOUR PRIVATE KEY TO STDOUT!!**  
If you didn't set password yet, use --wallet_decrypt_unsafe --wallet=`<wallet>`

### --wallet_destroy --wallet=`<wallet>`
Destroys `<wallet>` and all keys it contains

### --wallet_import  --file=`<filepath>` --wallet=`<wallet>` --password=`<password>`
Imports keys in `<filepath>` using `<password>` in to `<wallet>`

### --wallet_list
Dumps wallet IDs and public keys

### --wallet_remove --wallet=`<wallet>` --account=`<account>`
Remove `<account>` from `<wallet>`

### --wallet_representative_get --wallet=`<wallet>`
Prints default representative for `<wallet>`

### --wallet_representative_set --wallet=`<wallet>` --account=`<account>`
Set `<account>` as default representative for `<wallet>`