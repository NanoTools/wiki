**To enable RPC for node edit [config.json](https://github.com/clemahieu/raiblocks/wiki/config.json) after first launch**   
./rai_node --daemon  
sed -i 's/"rpc_enable": "false"/"rpc_enable": "true"/g' ~/RaiBlocks/config.json   
sed -i 's/"enable_control": "false"/"enable_control": "true"/g' ~/RaiBlocks/config.json   

**Launch rai_node in the background**   
./rai_node --daemon >./rai_node.log 2>&1 &   

**Check if RPC is enabled with curl**   
curl -g -d '{ "action": "block_count" }' [::1]:7076   

**To stop node, use**   
curl -g -d '{ "action": "stop" }' [::1]:7076   

To manage node, use [RPC commands](https://github.com/clemahieu/raiblocks/wiki/RPC-protocol) or [CLI](https://github.com/clemahieu/raiblocks/wiki/Command-line-interface)   

# Ubuntu 16.04 LTS Server
sudo apt-get update && sudo apt-get upgrade   
sudo apt-get install git cmake g++ curl   
### Building static Boost
wget -O boost_1_63_0.tar.gz http://sourceforge.net/projects/boost/files/boost/1.63.0/boost_1_63_0.tar.gz/download   
tar xzvf boost_1_63_0.tar.gz   
cd boost_1_63_0   
./bootstrap.sh   
./b2 --prefix=../[boost] link=static install
### Building rai_node
git clone --recursive https://github.com/clemahieu/raiblocks.git rai_build   
cd rai_build   
cmake -DACTIVE_NETWORK=rai_live_network -DCMAKE_BUILD_TYPE=Release -DBOOST_ROOT=../[boost] -G "Unix Makefiles"   
make rai_node   
cp rai_node ../rai_node && cd .. && ./rai_node --diagnostics   


# Debian 9 Stretch
apt-get update && apt-get upgrade   
apt-get install git cmake g++ libboost-all-dev curl   
### Building rai_node
git clone --recursive https://github.com/clemahieu/raiblocks.git rai_build   
cd rai_build   
cmake -DACTIVE_NETWORK=rai_live_network -DCMAKE_BUILD_TYPE=Release -G "Unix Makefiles"   
make rai_node   
cp rai_node ../rai_node && cd .. && ./rai_node --diagnostics   
