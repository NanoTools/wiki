# Building on Windows
* Install QT5

## MSYS
* Download MSYS/MinGW installer
* Inside MinGW Installation Manager install -> Basic Setup
* "msys-base bin" -> Mark For Installation
* "msys-wget bin" -> Mark For Installation
* Install to [msys]
* Installation -> Apply Changes -> Apply
* Exit installer

## MinGW-w64
* Download MinGW-w64 installer
* Change install folder to [msys]
* Finish installer

## Other Install
* CMake 3.0.1 source extracted to [cmake.src]
* Boost 1.55 source extracted to [boost.src]
* Googletest 1.7 source extracted to [gtest.src]
* Cryptopp source extracted to [cryptopp.src]
* RaiBlocks source source in [rai.src]

## Run MSYS shell
* Run "c:/MinGW/msys/1.0/msys.bat"

## Build cmake
* Inside directory [cmake.build]
* Run "[cmake.src]/configure --prefix=[cmake]"
* Run "make"
* Run "make install"

## Build Boost
* Inside directory [boost.src]
* Run ./bootstrap --with-toolset=mingw
* Edit the file project-config.jam and replace 'mingw' by 'gcc
* Run "./b2 --without-context --without-coroutine --build-dir=[boost.build] --prefix=[boost] link=static install"

## Build Googletest
* Inside directory [gtest.build]
* Run "[cmake]/bin/cmake -G "Unix Makefiles" [gtest.src]"
* Run "make"

## Build cryptopp
* Inside directory [cryptopp.src]
* Run "make CXXFLAGS=-DCRYPTOPP_DISABLE_AESNI"
* Run "make install PREFIX=[cryptopp]"

## Build RaiBlocks
* Inside directory [rai.build]
* Run "../cmake-3.0.2/bin/cmake -G "Unix Makefiles" -D GTEST_INCLUDE_DIR:PATH=../gtest-1.7.0.src/include -D GTEST_LIBRARY:FILEPATH=/c/Users/colin/gtest-1.7.0.build/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/c/Users/colin/gtest-1.7.0.build/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../rai.src -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final.src -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp562 -D BOOST_ROOT:PATH=../boost_1_56_0 -D Qt5_DIR=/c/Qt/5.3/mingw482_32/lib/cmake/Qt5 ../rai.src"

## Building a package
cpack -G "ZIP"