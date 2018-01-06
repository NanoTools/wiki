**Wallet crashes at start**
* Check if your system supports IPv6

**Missing transactions**
* Check if wallet status is locked. If true, unlock wallet with password
* Check if block count matches [raiblocks.net](https://raiblocks.net).  Advanced -> Block count.  Expect this to take ~24h from a brand new install.
* Check for connectivity.  Advanced -> Peers -> Refresh and make sure IPs are listed
* Check for correct wallet version.
* Check for and disable your router's "IP Flood Detection" feature
* Restart wallet and wait for synchronization to complete
* Make sure accounts are not in more than one wallet

**Api-ms-win-crt-runtime-l1-1-0.dll missing**
* Install Universal C Runtime for [your Windows version](https://support.microsoft.com/en-us/help/3118401/update-for-universal-c-runtime-in-windows)

**VCRUNTIME140.dll missing**
* For Windows 64-bit
[Visual C++ Redistributable for Visual Studio 2015 Update 3 (64-bit)](https://download.microsoft.com/download/6/A/A/6AA4EDFF-645B-48C5-81CC-ED5963AEAD48/vc_redist.x64.exe)
* For Windows 32-bit
[Visual C++ Redistributable for Visual Studio 2015 Update 3 (32-bit)](https://download.microsoft.com/download/6/A/A/6AA4EDFF-645B-48C5-81CC-ED5963AEAD48/vc_redist.x86.exe)