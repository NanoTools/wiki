
### --account_create --wallet=`<wallet>`
Insert next deterministic key in to `<wallet>`

### --account_get --key=`<key>`
Get account number for the `<key>`

### --account_key --account=`<account>`
Get the public key for `<account>`

### --daemon
Start node daemon

### --data_path=`<path>` 
Use the supplied `<path>` as the data directory

### --debug_block_count
Display the number of block

### --debug_bootstrap_generate
Generate bootstrap sequence of blocks

### --debug_dump_representatives
List representatives and weights

### --debug_frontier_count
Display the number of accounts

### --debug_mass_activity
Generates fake debug activity

### --debug_profile_generate
Profile work generation

### --debug_profile_verify
Profile work verification

### --debug_profile_kdf
Profile kdf function

### --debug_verify_profile
Profile signature verification

### --debug_profile_sign
Profile signature generation

### --debug_xorshift_profile
[Disabled] Profile xorshift algorithms

### --debug_opencl --platform=`<platform>` --device=`<device>` --threads=`<threads>`
_[Draft]_ Profile OpenCL work generation for `<device>` on `<platform>` using `<threads>` count. To retrieve available platforms & devices run --diagnostics

### --diagnostics
Run internal diagnostics

### --help
Print out options

### --key_create
Generates a adhoc random keypair and prints it to stdout

### --key_expand --key=`<key>`
Derive public key and account number from `<key>`

### --snapshot
Compact database and create snapshot, functions similar to vacuum but does not replace the existing database

### --vacuum
Compact database. If data_path is missing, the database in data directory is compacted

### --version    
Prints out version

### --vote_dump
Dump most recent votes from representatives

### --wallet_add_adhoc --wallet=`<wallet>` --key=`<key>`
Insert `<key>` in to `<wallet>`

### --wallet_create
Creates a new wallet and prints the ID

### --wallet_change_seed --wallet=`<wallet>` --key=`<key>`
Changes seed for `<wallet>` to `<key>`

### --wallet_decrypt_unsafe --wallet=`<wallet>` --password=`<password>`
Decrypts `<wallet>` using `<password>`  
**!!THIS WILL PRINT YOUR PRIVATE KEY AND SEED TO STDOUT!!**  
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