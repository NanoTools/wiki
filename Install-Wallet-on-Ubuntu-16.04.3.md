### CLEAN UBUNTU 16.04.3 X64

I had to piece this together from other wallet install instructions. The QT5 cam from ZCoin github. The use of Environment variable BOOST_ROOT I picked up from a BITShares doc online. I am running ./b2 as sudo since there was an include folder that I otherwise did not have access to create.

I found the -q parameter useful while installing b2 as it forces the install to stop at the first error letting you see which dependencies you are missing.

    export BOOST_ROOT=$HOME/opt/boost_1_63_0

    sudo apt-get update
    sudo apt install git
    sudo apt install cmake
    sudo apt-get install autotools-dev build-essential g++ python-dev libicu-dev libbz2-dev

### INSTALL BOOST 1.63.0

    wget -O boost_1_63_0.tar.gz http://sourceforge.net/projects/boost/files/boost/1.63.0/boost_1_63_0.tar.gz/download

    tar xzvf boost_1_63_0.tar.gz
    cd boost_1_63_0

    ./bootstrap.sh "--prefix=$BOOST_ROOT"


    export BOOST_BUILD=$HOME/opt/boost_1_63_0.BUILD

    sudo ./b2 --prefix=$BOOST_ROOT --build-dir=$BOOST_BUILD link=static install

### install QT5

    sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler

### Install RAI_WALLET

    cd ~
    git clone https://github.com/clemahieu/raiblocks
    cd raiblocks
    git submodule update --init --recursive
    cmake -G "Unix Makefiles" -DRAIBLOCKS_GUI=ON -DBOOST_ROOT="$BOOST_ROOT"
    make rai_wallet
    cp rai_wallet .. && cp librai_lib.so  .. && cd .. && ./rai_wallet

Next time you can run your wallet by running `./rai_wallet` in your home folder. Or simply double click the file in your file browser. 

Thanks,
Cryptohuh