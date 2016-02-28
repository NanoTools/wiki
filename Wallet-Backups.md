Wallet backups are created in RaiBlocks/backups written on 5 minute intervals.

Backup Location:  
Windows: C:\Users\<user>\AppData\Local\RaiBlocks\backup  
OSX: /Users/<user>/Library/RaiBlocks/backup  
Linux: ~/RaiBlocks/backup  

The default password is empty.  At the top of your wallet it will tell you if your wallet has an empty password.  It can be changed in Settings -> Change Password.  If you change your password the next backup interval will contain the newly encrypted wallet.

The wallet can be restored in the GUI via Advanced -> Accounts -> Import wallet  
or on the command line with --wallet_import