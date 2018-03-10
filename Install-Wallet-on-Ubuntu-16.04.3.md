### Install dependencies

    sudo apt-get update && sudo apt-get upgrade
    sudo apt-get install git cmake g++ curl wget
  
### Build Boost 1.66.0

    wget -O boost_1_66_0.tar.gz https://netix.dl.sourceforge.net/project/boost/boost/1.66.0/boost_1_66_0.tar.gz
    tar xzvf boost_1_66_0.tar.gz
    cd boost_1_66_0
    ./bootstrap.sh --with-libraries=filesystem,iostreams,log,program_options,thread
    ./b2 --prefix=../[boost] link=static install   
    cd ..

### Install QT5

    sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler

### Build nano_wallet

    git clone --recursive https://github.com/nanocurrency/raiblocks.git rai_build   
    cd rai_build
    git submodule update --init --recursive
    cmake -G "Unix Makefiles" -DRAIBLOCKS_GUI=ON -DBOOST_ROOT=../[boost]/
    make nano_wallet
    cp nano_wallet ../nano_wallet && cd .. 

### Run nano_wallet

    ./nano_wallet

### Troubleshooting

* **This application failed to start because it could not find or load the Qt platform plugin "xcb".**

If you get this error, make sure you have QT5 installed. If it's installed, locate the file 'libqxcb.so' on your system and then tell nano_wallet where this file can be found (set it to the 'plugins' directory).

    locate libqxcb.so
    # returns /usr/lib/qt/plugins/platforms/libqxcb.so or something similar
    export QT_PLUGIN_PATH=/usr/lib/qt/plugins
    nano_wallet

If you don't want to run this each time you can setup an alias to do this for you:

    echo 'alias nano_wallet="QT_PLUGIN_PATH=/usr/lib/qt/plugins nano_wallet"' >> ~/.bashrc
    source ~/.bashrc

* **Error starting nano exception while running wallet: No such node (Wallet)**

If you get this error, it might be related to pre-existing configuration file issues on your system. You can try the following to generate a fresh configuration (your existing/older configuration will be under ~/RaiBlocks.old). **Please be careful with the following if you already run a wallet, as these details will be forgotten by the nano_wallet due to starting with a fresh configuration:**

    mv ~/RaiBlocks{,.old}
    nano_wallet

* **Wallet crashes with an `Aborted (core dumped)` error**

This may be related to a display issue. Try setting the environment variable `GDK_BACKEND=x11` before running nano_wallet.

    GDK_BACKEND=x11 ./nano_wallet
