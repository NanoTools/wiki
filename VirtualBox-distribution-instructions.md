## Downloads
* VirtualBox
* FreeBSD 10.0

## VM configurations
* Type: FreeBSD 64bit
* Memory 512mb
* HDD 32GB dynamic VMDK

## Installation
* Ports Tree
* Entire disk
* No startup services

## Setup
* Run "pkg install virtualbox-ose-kmod"
* Run "pkg install virtualbox-ose-additions"
* Run "pkg install xorg"
* Run "pkg install xfce"

## Add startup services to /etc/rc.conf  
hald_enable="YES"  
dbus_enable="YES"  

reboot
startxfce4