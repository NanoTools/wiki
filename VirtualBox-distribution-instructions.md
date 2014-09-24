## Downloads
* SuseStudio

## VM configurations
* Type: ArchLinux 64bit
* Memory 512mb
* HDD 32GB dynamic VMDK

## Installation


## Setup
* Run "pkg install virtualbox-ose-kmod"
* Run "pkg install virtualbox-ose-additions"
* Run "pkg install xorg"
* Run "pkg install xfce"

## Add startup services to /etc/rc.conf  
hald_enable="YES"  
dbus_enable="YES"  

## Allow kernel shared memory in /etc/sysctl.conf
* kern.ipc.shm_allow_removed=1

reboot
startxfce4