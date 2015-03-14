# Building on OSX
* Install QT5

## Required source
* Boost 1.55 extracted to [boost.src]
* Googletest 1.7 extracted to [gtest.src]
* cryptopp extracted to [cryptopp.src]
* cpp-netlib extracted to [cppnetlib.src]
* RaiBlocks source in [rai.src]

## Build cmake
* Inside [cmake.build]
* Run "[cmake.src]/configure --prefix=[cmake]"
* Run "make"
* Run "make install"

## Build Boost
* Inside [boost.src]
* Run "./bootstrap.sh
* Run "./b2 --prefix=[boost] link=static install"

## Build Googletest
* Inside directory [gtest.build]
* Run "[gtest.src]/configure"
* Run "make"

## Build cryptopp
* Inside directory [cryptopp.src]
* Run "make"
* Run "make install PREFIX=[cryptopp]"

## Cppnetlib source only  
* Set CPPNETLIB_INCLUDE_DIRS=[cppnetlib.src]  

## Build RaiBlocks
* Inside directory [rai.build]
* Run "../cmake-3.0.1/bin/cmake -G "Unix Makefiles" -D GTEST_INCLUDE_DIR:PATH=../gtest-1.7.0.src/include -D GTEST_LIBRARY:FILEPATH=/Users/colin/Desktop/gtest-1.7.0.build/lib/.libs/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/Users/colin/Desktop/gtest-1.7.0.build/lib/.libs/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../rai.src -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final.src -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp562 -D BOOST_ROOT=../boost_1_56 -D Qt5_DIR=../../Qt/5.3/clang_64/lib/cmake/Qt5 ../rai.src"

## Building a package
* cpack -G "DragNDrop"