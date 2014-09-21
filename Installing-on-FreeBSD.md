# Building on FreeBSD

## Other Install
* CMake 3.0.1 source extracted to [cmake.src]
* Boost 1.55 source extracted to [boost.src]
* Googletest 1.7 source extracted to [gtest.src]
* LevelDB (zalanyib/leveldb-mingw) source extracted to [leveldb.src]
* Cryptopp source extracted to [cryptopp.src]
* mu_coin source source in [mu_coin.src]
* Run "pkg install Qt5"

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
* Inside gtest-build run "cmake -G "Unix Makefiles" /usr/src/gtest
* Then run "make"

## Build cppnetlib
* In the cppnetlib directory run 'cmake -G "Unix Makefiles"'
* Then run "make"

## Build Cryptopp
* In the cryptopp directory run "make"

## Build mu_coin
* Run "mkdir mu_coin_build"
* Inside mu_coin_build run "cmake -G "Unix Makefiles" -D GTEST_LIBRARY:FILEPATH=/home/colin/Desktop/gtest-build/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/home/colin/Desktop/gtest-build/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../mu_coin -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp -D CRYPTOPP_INCLUDE_DIR:PATH=.. -DLevelDB_LIBRARY:FILEPATH=/home/colin/Desktop/leveldb-1.15.0/libleveldb.a -DLevelDB_INCLUDE_PATH:PATH=../leveldb-1.15.0/include ../mu_coin"