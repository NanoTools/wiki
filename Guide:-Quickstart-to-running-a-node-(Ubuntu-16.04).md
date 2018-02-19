### Install boost library
````
apt-get update
apt-get install libboost-all-dev
````

### Download and extract nano node
````
cd ~
wget https://github.com/nanocurrency/raiblocks/releases/download/10.0.1/rai-10.0.1-Linux-x86_64.tar.bz2
tar xvf rai-10.0.1-Linux-x86_64.tar.bz2
````

### Initiate rai_node to generate ~/RaiBlocks 
````
 ./rai-10.0.1-Linux/bin/rai_node --daemon
````
_Press ctrl+c to kill process_

### Update config.json
````
vim RaiBlocks/config.json
````
Change: "rpc_enable": "true"
Save and quit


### Create service file
````
sudo touch /etc/systemd/system/rai_node.service   
sudo chmod 664 /etc/systemd/system/rai_node.service   
sudo vim /etc/systemd/system/rai_node.service  
````

### Fine the path of the rai_node binary, as well as the user it will be run by
````
cd ~/rai-10.0.1-Linux/bin/
pwd -P # Example: /home/stanley/rai-10.0.1-Linux/bin <= write down this path

ls -l #Example: -rwxr-xr-x 1 **stanley stanley** 8.9M Feb 16 02:25 rai_node <= write down the user and group to the left of rai_node, this should be the same as your username
````

### Service file
````
[Unit]
Description=RaiBlocks node service
After=network.target

[Service]
ExecStart=/home/stanley/rai-10.0.1-Linux/bin/rai_node --daemon #Update this with the link copied from the last step
Restart=on-failure
User=stanley #This user from the last step
Group=stanley #The group from the last step

[Install]
WantedBy=multi-user.target
````

### Start the service
`sudo service rai_node start`

### Enable the node to run on boot
`sudo systemctl enable rai_node`


### Link to rai_node
` ln -s ~/rai-10.0.1-Linux/bin/rai_node /usr/local/sbin/rai_node`

### Voila!
You should now have a brand new node up and running, and the blocks syncing.

### Check Status
`rai_node --debug_block_count #This will show you how far along the node is to syncing the blocks`