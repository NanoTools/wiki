* [Alternatively, use paper wallet generator](https://numtel.github.io/rai-paper-wallet/)

### Disclaimer

This guide is offered as-is, with no guarantees of any kind. Please do be careful.

# What this guide covers

This guide explains how to create a cold or air-gapped wallet. If you wish to start from a machine that already has a running hot wallet, start at step 0. If you've already got rai wallet installed on your air-gapped machine, start at step 4.

# What this guide does not cover

* Why you should (or shouldn't) do this
* Any wallet other than the official, desktop Rai wallet
* How the Rai wallet works
* How Rai works

# User data locations

* Windows: C:\Users<user>\AppData\Local\RaiBlocks
* OSX: /Users/username/Library/RaiBlocks
* Linux: ~/RaiBlocks

# Steps

0. We assume you have your hot wallet loaded.
1. Backup your hot wallet. This can be done in one of three ways. Either (a) by going to `Accounts->Backup/Clipboard wallet seed` and then storing that seed somewhere, (b) by copying one of the backups in the user data location, or (c) by simply copying ALL of the user data to some other folder.  To avoid having to re-sync, I recommend option (c). If you never synced, pick your poison.
2. Close rai wallet, make sure it's closed.  
3. Delete everything in your RaiBlocks user data directory.
4. Open rai wallet. Create new account(s) if necessary for the number of cold accounts you want.
5. Backup the seed and address(es), again by going to `Accounts->Backup/Clipboard wallet seed`. This is your cold wallet seed--it's the only thing you really need. It's also worth taking down the account addresses by using the `copy` button in the top right of the window.
6. Repeat step 2 and 3.  Did you store your seed somewhere? Good.
7. To get your hot wallet back: If you used option (c), just copy the files back into place. The other options should use the import feature at `Accounts-<Import wallet`.  Boom, you're done.

# Additional Notes

Keep a copy of the rai wallet software with your seed. At the very least, note the version that you used.  And *do not lose your seed!*  *Do not give it out to anyone, no matter how cute!*