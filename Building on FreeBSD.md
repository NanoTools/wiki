****Incomplete****

## Other Install
* CMake 3.0.1 source extracted to [cmake.src]
* Boost 1.55 source extracted to [boost.src]
* Googletest 1.7 source extracted to [gtest.src]
* LevelDB (zalanyib/leveldb-mingw) source extracted to [leveldb.src]
* Cryptopp source extracted to [cryptopp.src]
* Cppnetlib source extracted to [cppnetlib.src]
* mu_coin source source in [mu_coin.src]

# Packages
* Run "pkg install Qt5"
* Run "pkg install gmake"
* Run "pkg install swt"

## Build cmake
* Inside directory [cmake.build]
* Run "[cmake.src]/configure --prefix=[cmake]"
* Run "make"
* Run "make install"

## Build Boost
* Inside directory [boost.src]
* Run ./bootstrap --with-toolset=clang
* Run "./b2 --without-context --without-coroutine --build-dir=[boost.build] --prefix=[boost] link=static install"

## Build Googletest
* Run "mkdir gtest-build"
* Inside gtest-build run "../cmake-3.0.2/bin/cmake -G "Unix Makefiles" [cmake.src]
* Then run "make"

## Build Cryptopp
* In the cryptopp directory run "CC=clang CXX=clang++ PREFIX=[cryptopp] gmake install"

## Build leveldb
* Inside [leveldb.src]
* Run "CC=clang CXX=clang++ gmake"

## Build mu_coin
* Run "mkdir mu_coin_build"
* Inside mu_coin_build run "cmake -G"Unix Makefiles" -DBOOST_ROOT=/home/colin/boost_1_56_0 -DGTEST_INCLUDE_DIR=/home/colin/gtest-1.7.0.src/include -DGTEST_LIBRARY=/home/colin/gtest-build/libgtest.a -D GTEST_MAIN_LIBRARY=/home/colin/gtest-build/libgtest_main.a -DCMAKE_MODULE_PATH:PATH=../mu_coin.src -Dcppnetlib_DIR=../cpp-netlib-0.11.0-final -DCRYPTOPP_ROOT_DIR=../cryptopp562 -DLevelDB_LIBRARY=/home/colin/Desktop/leveldb.src/libleveldb.a -DLevelDB_INCLUDE_PATH=/home/colin/leveldb/include ../mu_coin.src"