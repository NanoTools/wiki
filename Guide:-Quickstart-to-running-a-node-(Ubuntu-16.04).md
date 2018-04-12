### Install boost library
````
apt-get update
apt-get install libboost-all-dev
````

### (Optional) Build and Install boost v1.66 instead (Ubuntu repo has v1.58)
````
wget https://dl.bintray.com/boostorg/release/1.66.0/source/boost_1_66_0.tar.bz2
tar --bzip2 -xf boost_1_66_0.tar.bz2
cd boost_1_66_0
./bootstrap.sh
sudo ./b2 install
````
### Download and extract nano node
````
cd ~
wget https://github.com/nanocurrency/raiblocks/releases/download/V11.2/nano-11.2.0-Linux.tar.bz2
tar xvf nano-11.2.0-Linux.tar.bz2
````

### Initiate rai_node to generate ~/RaiBlocks 
````
 ./rai-11.2.0-Linux/bin/rai_node --daemon
````
_Press ctrl+c to kill process_

### Update config.json
````
nano ~/RaiBlocks/config.json
````
Change: "rpc_enable": "true"
Save and quit


### Find the path of the rai_node binary, as well as the user it will be run by
````
cd ~/rai-11.2.0-Linux/bin/
pwd -P
````
This should output something similar to: /home/stanley/rai-11.2.0-Linux/bin
Write down this path for our service file in a future step

````
ls -l
````
This should output something similar to: -rwxr-xr-x 1 stanley stanley 8.9M Feb 16 02:25 rai_node
Write down the user and group (in this example, both the user and group is stanley) to the left of rai_node, this should be the same as your username

### Create service file
````
sudo touch /etc/systemd/system/rai_node.service   
sudo chmod 664 /etc/systemd/system/rai_node.service   
sudo nano /etc/systemd/system/rai_node.service  
````

### Service file
````
[Unit]
Description=RaiBlocks node service
After=network.target

[Service]
ExecStart=/home/stanley/rai-11.2.0-Linux/bin/rai_node --daemon #Update this with the link copied from the last step
Restart=on-failure
User=stanley #This user from the last step
Group=stanley #The group from the last step

[Install]
WantedBy=multi-user.target
````

Be sure to remove the comments (the parts starting at #) as they may cause problems.

### Start the service
````
sudo service rai_node start
````

### Enable the node to run on boot
````
sudo systemctl enable rai_node
````

### Create a symlink to rai_node to easily access later
````
ln -s ~/rai-11.2.0-Linux/bin/rai_node /usr/local/sbin/rai_node
````

### Voila!
You should now have a brand new node up and running, and the blocks syncing.

### Check Status
````
rai_node --debug_block_count
````
This will show you how far along the node is to syncing the blocks. You can compare this to the current block count at [https://www.nanode.co/blocks](https://www.nanode.co/blocks) to see how far along the syncing process your are