Install

    cmake
    base-devel
    boost

Then

    git clone -b arm https://github.com/drizzt/raiblocks
    cd raiblocks
    cmake -DACTIVE_NETWORK=rai_live_network -DCMAKE_BUILD_TYPE=Release .
    make rai_node