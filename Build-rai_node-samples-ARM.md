**[Running node as a service](https://github.com/nanocurrency/raiblocks/wiki/Running-rai_node-as-a-service)**
    
**To manage node, use [RPC commands](https://github.com/nanocurrency/raiblocks/wiki/RPC-protocol) or [CLI](https://github.com/nanocurrency/raiblocks/wiki/Command-line-interface)**   

***

# ArchlinuxARM 64bit
### Dependency Build Instructions

```bash
pacman -Syu  
pacman -S base-devel git gcc cmake curl wget
```

### Building static Boost

```bash
wget -O boost_1_66_0.tar.gz http://sourceforge.net/projects/boost/files/boost/1.66.0/boost_1_66_0.tar.gz/download   
tar xzvf boost_1_66_0.tar.gz   
cd boost_1_66_0   
./bootstrap.sh   
./b2 --prefix=../[boost] link=static install   
cd ..
```

### Building rai_node

```bash
git clone --recursive https://github.com/nanocurrency/raiblocks.git rai_build   
cd rai_build   
cmake -DBOOST_ROOT=../[boost] -G "Unix Makefiles"   
make rai_node   
cp rai_node ../rai_node && cd .. && ./rai_node --diagnostics   
```