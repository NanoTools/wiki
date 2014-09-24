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
* In [cppnetlib.build] run 'cmake -G "Unix Makefiles" -DCMAKE_INSTALL_PREFIX=[cppnetlib] [cppnetlib.src]'
* Run "make"
* Run "make install"

## Build Cryptopp
* In [cryptopp.src] run "make"
* Run "PREFIX=[cryptopp] make install"

## Build mu_coin
* Run "mkdir mu_coin_build"
* Inside mu_coin_build run "cmake -G "Unix Makefiles" -D GTEST_LIBRARY:FILEPATH=/home/colin/Desktop/gtest-build/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/home/colin/Desktop/gtest-build/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../mu_coin -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp -D CRYPTOPP_INCLUDE_DIR:PATH=.. -DLevelDB_LIBRARY:FILEPATH=/home/colin/Desktop/leveldb-1.15.0/libleveldb.a -DLevelDB_INCLUDE_PATH:PATH=../leveldb-1.15.0/include ../mu_coin"