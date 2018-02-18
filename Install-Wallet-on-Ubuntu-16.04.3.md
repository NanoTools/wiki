### CLEAN UBUNTU 16.04.3 X64

I had to piece this together from other wallet install instructions. The QT5 cam from ZCoin github. The use of Environment variable BOOST_ROOT I picked up from a BITShares doc online. I am running ./b2 as sudo since there was an include folder that I otherwise did not have access to create.

I found the -q parameter useful while installing b2 as it forces the install to stop at the first error letting you see which dependencies you are missing.

    export BOOST_ROOT=$HOME/opt/boost_1_66_0

    sudo apt-get update
    sudo apt install git
    sudo apt install cmake
    sudo apt-get install autotools-dev build-essential g++ python-dev libicu-dev libbz2-dev

### INSTALL BOOST 1.66.0

    wget -O boost_1_66_0.tar.gz http://sourceforge.net/projects/boost/files/boost/1.66.0/boost_1_66_0.tar.gz/download

    tar xzvf boost_1_66_0.tar.gz
    cd boost_1_66_0

    ./bootstrap.sh "--prefix=$BOOST_ROOT"


    export BOOST_BUILD=$HOME/opt/boost_1_66_0.BUILD

    sudo ./b2 --prefix=$BOOST_ROOT --build-dir=$BOOST_BUILD link=static install

### install QT5

    sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler

### Build NANO_WALLET

    cd ~
    git clone https://github.com/clemahieu/raiblocks
    cd raiblocks
    git submodule update --init --recursive
    cmake -G "Unix Makefiles" -DRAIBLOCKS_GUI=ON -DBOOST_ROOT="$BOOST_ROOT"
    make nano_wallet

### Copy/install the nano_wallet binary to /usr/local/bin so it's on your $PATH and try and run it

    sudo cp nano_wallet /usr/local/bin/
    nano_wallet

If the above works, then you should be able to open a terminal and run 'nano_wallet' anytime you want to run the wallet from here on.

### Troubleshooting

**This application failed to start because it could not find or load the Qt platform plugin "xcb".**

If you get this error, make sure you have QT5 installed. If it's installed, locate the file 'libqxcb.so' on your system and then tell nano_wallet where this file can be found (set it to the 'plugins' directory).

    locate libqxcb.so
    # returns /usr/lib/qt/plugins/platforms/libqxcb.so or something similar
    export QT_PLUGIN_PATH=/usr/lib/qt/plugins
    nano_wallet

If you don't want to run this each time you can setup an alias to do this for you:

    echo 'alias nano_wallet="QT_PLUGIN_PATH=/usr/lib/qt/plugins nano_wallet"' >> ~/.bashrc
    source ~/.bashrc

**Error starting nano exception while running wallet: No such node (Wallet)**

If you get this error, it might be related to pre-existing configuration file issues on your system. You can try the following to generate a fresh configuration (your existing/older configuration will be under ~/RaiBlocks.old). **Please be careful with the following if you already run a wallet, as these details will be forgotten by the nano_wallet due to starting with a fresh configuration:**

    mv ~/RaiBlocks{,.old}
    nano_wallet

### Uninstall the wallet

    sudo rm /usr/local/bin/nano_wallet

( note: your configuration should still exist in ~/RaiBlocks/ )