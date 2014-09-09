# Building on Windows
* Install QT5

## MinGW
* Download MinGW
* Inside MinGW Installation Manager install -> Basic Setup
* "mingw-developer-toolkit" -> Mark For Installation
* "mingw32-base bin" -> Mark For Installation
* "mingw32-gcc-g++ bin" -> Mark For Installation
* "msys-base bin" -> Mark For Installation
* Installation -> Apply All Changes
* Add to system environment variables "c:\MinGW\bin" "c:\MinGW\msys\1.0\bin"
* Create "c:\MinGW\msys\1.0\etc\fstab" and add the line "C:\MinGW /mingw"

## Other Install
* CMake 3.0.1 extracted to [cmake.src]
* Boost 1.55 extracted to [boost.src]
* Googletest 1.7 extracted to [gtest.src]
* LevelDB (zalanyib/leveldb-mingw) extracted to [leveldb.src]
* Cryptopp extracted to [cryptopp.src]
* mu_coin source in [mu_coin.src]

## Run MSYS shell
* Run "c:/MinGW/msys/1.0/msys.bat"
* Run "export PATH=$PATH:/c/MinGW/bin/" inside MSYS shell to add compiler tools to path

## Build cmake
* Inside directory [cmake.build]
* Run "[cmake.src]/configure --prefix=[cmake]"
* Run "make"
* Run "make install"

## Build Boost
* Inside directory [boost.src]
* Run ./bootstrap --with-toolset=mingw
* Edit the file project-config.jam and replace 'mingw' by 'gcc
* Run "./b2 --without-context --without-coroutine --build-dir=../boost_1_56_0.build --prefix=/home/colin/boost_1_56_0 link=static install"

## Build LevelDB
* Inside directory [leveldb.src]
* Run "make"

## Build Googletest
* Inside directory [gtest.build]
* Run "[gtest.src]/configure"
* Run "make"

## Build cryptopp
* Inside directory [cryptopp.build]
* Run "cmake -G "Unix Makefiles" [cryptopp.build] -DBOOST_ROOT=[boost]"
* Run "make install PREFIX=[cryptopp]"

## Build mu_coin
* Inside directory [mu_coin.build]
* Run "$ ../cmake-3.0.1/bin/cmake -G "Unix Makefiles" -D GTEST_INCLUDE_DIR:PATH=../gtest-1.7.0.src/include -D GTEST_LIBRARY:FILEPATH=/Users/colin/Desktop/gtest-1.7.0.build/lib/.libs/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/Users/colin/Desktop/gtest-1.7.0.build/lib/.libs/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../mu_coin -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final.src -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp562.src -D LevelDB_LIBRARY:FILEPATH=/Users/colin/Desktop/leveldb-1.15.0.src/libleveldb.a -D LevelDB_INCLUDE_PATH:PATH=../leveldb-1.15.0.src/include -D BOOST_ROOT:PATH=../boost_1_56_0 -D Qt5_DIR=../../Qt/5.3/clang_64/lib/cmake/Qt5 ../mu_coin.src"