## RaiBlocks folder contains:

- wallets backup
- log files
- blockchain
- config.json

## Locations across platforms:


    Windows: C:\Users\<user>\AppData\Local\RaiBlocks\
    OSX: /Users/<user>/Library/RaiBlocks/
    Linux: /home/<user>/RaiBlocks/

Some users desire to change the blockchain download location, be it as a result of a full disk, interrupts impacting responsiveness or whatever - whilst a solution is available for the nogui rai_node (see https://github.com/nanocurrency/raiblocks/issues/79), no concrete solution is available for the GUI client. However, a workaround can be acheived via the use of symbolic links. Here is a short and sweet tutorial for the windows builds - I trust that Linux users will know how to create symlinks :] (as for OSX, I don't own a machine that runs it).
1. Rename/delete the RaiBlocks folder in your appdata Local folder (if you haven't run the wallet yet, skip this step). This is necessary because the command to create a symbolic link in windows will fail if the the input directory already exists.
2. Decide on where you want to store the blockchain and create a symbolic link. The command is (in an administrative command-prompt): `mklink /d "C:\Users\<user>\AppData\Local\RaiBlocks\" "E:\Some\Other\Directory"`. This command creates a symbolic link for a directory (/d) that 'redirects' all requests for files/directories in the Local\RaiBlocks folder to the Other\Directory. This means that a file created in the input directory will actually be in the output directory (on the other disk).
3. Verify it works. Create a file in your RaiBlocks folder in your appdata, and you should see it appear in the directory you linked it to (and vice-versa). If you have old wallets or a partially-downloaded blockchain, copy them back into the local directory. Start the wallet.