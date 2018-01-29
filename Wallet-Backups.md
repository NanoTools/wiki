# Backup:
All accounts you create in your wallet are tied together by a wallet 'seed'.  This seed can be used to regenerate your wallet in case of data loss and it also can be used to access and send from any of the accounts so it's important to keep this seed safe.

We recommend backing up the seed by writing it on a piece of paper, perhaps twice, and storing it in a secure fire/water proof location.  Never put the seed into a file unencrypted.

You can copy the seed to your clipboard in the wallet by going to "Accounts" -> "Backup/Clipboard wallet seed"

If you need to reload this seed into your wallet in the future, you can do so through "Advanced" -> "Accounts" -> "Import wallet" and typing the seed into the "seed" box.  Confirm that you want to clear existing keys and then push "Import seed".

# Docker container backup:  
If you run a docker container, you can backup the seed via the command line.  First list the wallets attached to this node with the command:  

```bash
sudo docker run -it -v ~:/root clemahieu/rai_node /rai_node --wallet_list
```

Then you can list the wallet seed and adhoc private keys with the command:  
```bash
sudo docker run -it -v ~:/root clemahieu/rai_node /rai_node --wallet_decrypt_unsafe --wallet={{wallet}} --password={{password}}
```  
# Old ad-hoc wallets:
Wallet backups are created in RaiBlocks/backups written on 5-minute intervals.
## Backup Location:  
### Windows: 
```bash
C:\Users\<user>\AppData\Local\RaiBlocks\backup
```  

### OSX: 
```bash
/Users/<user>/Library/RaiBlocks/backup
```

### Linux: 
```bash
~/RaiBlocks/backup  
```
The default password is empty.  At the top of your wallet, it will tell you if your wallet has an empty password.  It can be changed in Settings -> Change Password.  If you change your password the next backup interval will contain the newly encrypted wallet.

The wallet can be restored in the GUI via Advanced -> Accounts -> Import wallet  
or on the command line with --wallet_import

From a docker node you can do:  
Pick or create a wallet to import the file in to.  

```bash
sudo docker run -it -v ~:/root clemahieu/rai_node /rai_node --wallet_list
```  
Copy the backup file into the RaiBlocks directory in your home directory.  

```bash
sudo docker run -it -v ~:/root clemahieu/rai_node /rai_node --wallet_import --file=/root/RaiBlocks/{{backup.json}} --wallet={{destination wallet}} --password={{password}}
```
or
```bash
sudo docker exec {{docker instance id}} /rai_node --wallet_list
```
```bash
sudo docker exec {{docker instance id}} /rai_node --wallet_import --file=/root/RaiBlocks/{backup.json} --wallet={{destination wallet}} --password={{password}}
```