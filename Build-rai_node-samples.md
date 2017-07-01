**To enable RPC for node edit [config.json](https://github.com/clemahieu/raiblocks/wiki/config.json) after first launch**   
./rai_node --daemon  
sed -i 's/"rpc_enable": "false"/"rpc_enable": "true"/g' ~/RaiBlocks/config.json   
sed -i 's/"enable_control": "false"/"enable_control": "true"/g' ~/RaiBlocks/config.json  
sed -i 's/"packet_delay_microseconds": "5000"/"packet_delay_microseconds": "500"/g' ~/RaiBlocks/config.json  

**Launch rai_node in the background (test mode)**   
./rai_node --daemon >./rai_node.log 2>&1 &   

**Check if RPC is enabled with curl**   
curl -g -d '{ "action": "block_count" }' [::1]:7076   

**To stop node, use**   
curl -g -d '{ "action": "stop" }' [::1]:7076   

**Launch rai_node as a service with system.d**   
sudo touch /etc/systemd/system/rai_node.service   
sudo chmod 664 /etc/systemd/system/rai_node.service   
sudo nano /etc/systemd/system/rai_node.service   
>_Paste your specific user, group, path settings (example)_   
    
    [Unit]
    Description=RaiBlocks node service
    After=network.target
    
    [Service]
    ExecStart=/path_to_rai_node/rai_node --daemon
    Restart=on-failure
    User=username
    Group=groupname

    [Install]
    WantedBy=multi-user.target
>_Start rai_node service_    

sudo service rai_node start

>_Enable at startup_    

sudo systemctl enable rai_node
    
    
**To manage node, use [RPC commands](https://github.com/clemahieu/raiblocks/wiki/RPC-protocol) or [CLI](https://github.com/clemahieu/raiblocks/wiki/Command-line-interface)**   

***

# Ubuntu 16.04 LTS Server
sudo apt-get update && sudo apt-get upgrade   
sudo apt-get install git cmake g++ curl   
### Building static Boost
wget -O boost_1_63_0.tar.gz http://sourceforge.net/projects/boost/files/boost/1.63.0/boost_1_63_0.tar.gz/download   
tar xzvf boost_1_63_0.tar.gz   
cd boost_1_63_0   
./bootstrap.sh   
./b2 --prefix=../[boost] link=static install   
cd ..
### Building rai_node
git clone --recursive https://github.com/clemahieu/raiblocks.git rai_build   
cd rai_build   
cmake -DBOOST_ROOT=../[boost] -G "Unix Makefiles"   
make rai_node   
cp rai_node ../rai_node && cd .. && ./rai_node --diagnostics   


# Debian 9 Stretch
apt-get update && apt-get upgrade   
apt-get install git cmake g++ libboost-all-dev curl   
### Building rai_node
git clone --recursive https://github.com/clemahieu/raiblocks.git rai_build   
cd rai_build   
cmake -G "Unix Makefiles"   
make rai_node   
cp rai_node ../rai_node && cd .. && ./rai_node --diagnostics   

# Ubuntu 16.04 on Digital Ocean Droplet ($5/Month 512Mb Ram, 1 Core, 20Gb SSD)
Sign up at digitalocean.com

Create Droplet

Add swap space - https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04

sudo fallocate -l 2G /swapfile  
sudo chmod 600 /swapfile  
sudo mkswap /swapfile  
sudo swapon /swapfile

sudo apt-get update  
sudo apt-get install g++  
sudo apt-get install make  
sudo apt install cmake

wget -O boost_1_63_0.tar.gz http://sourceforge.net/projects/boost/files/boost/1.63.0/boost_1_63_0.tar.gz/download  
tar xzvf boost_1_63_0.tar.gz  
cd boost_1_63_0  
./bootstrap.sh  
./b2 --prefix=../[boost] link=static install  
cd ..

git clone https://github.com/clemahieu/raiblocks.git  
cd raiblocks/

git submodule init  
git submodule update

cmake -DACTIVE_NETWORK=rai_live_network -DCMAKE_BUILD_TYPE=Release -DBOOST_ROOT=../[boost] -G "Unix Makefiles" 
 
make rai_node

./rai_node —-daemon &

check block count ./rai_node --debug_block_count
