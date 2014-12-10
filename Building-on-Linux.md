# Building on Linux

## Source code
* Cmake in [cmake.src]
* Boost in [boost.src]
* Google test in [gtest.src]
* cppnetlib in [cppnetlib.src]
* cryptopp in [cryptopp.src]
* leveldb in [leveldb.src]

## Build cmake
* Inside [cmake.build] run "[cmake.src]/configure --prefix=[cmake]"
* Run "make"
* Run "make install"

## Build boost
* Inside [boost.src]
* Run "./bootstrap.sh
* Run "./b2 --prefix=[boost] link=static install"

## Build Googletest
* Inside [gtest.build] run 'cmake -G "Unix Makefiles" [gtest.src]'
* Run "make"

## Build cppnetlib
* In [cppnetlib.build] run 'cmake -G "Unix Makefiles" -DBOOST_ROOT=[boost] -DCMAKE_INSTALL_PREFIX=[cppnetlib] [cppnetlib.src]'
* Run "make"
* Run "make install"

## Build Cryptopp
* In [cryptopp.src] run "make"
* Run "make PREFIX=[cryptopp] install"

## Build leveldb
* Inside [leveldb.src]
* Run "make"

## Build RaiBlocks
* Run "mkdir rai.build"
* Inside rai.build run "cmake -G "Unix Makefiles" -DBOOST_ROOT=[boost] -DGTEST_LIBRARY=[gtest.build]/libgtest.a -DGTEST_MAIN_LIBRARY=[gtest.build]/libgtest_main.a -DGTEST_INCLUDE_DIR=[gtest.src]/include -DCMAKE_MODULE_PATH=[rai.src] -Dcppnetlib_DIR=[cppnetlib] -DCRYPTOPP_ROOT_DIR=[cryptopp] -DLevelDB_LIBRARY=[leveldb.src]/libleveldb.a -DLevelDB_INCLUDE_PATH=[leveldb.src]/include [rai.src]"

## Building a package
* cpack -G "TBZ2"