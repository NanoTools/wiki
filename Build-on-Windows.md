# Building on Windows

## MSYS2
* Download MSYS2 64bit
* Install MSYS2
* Open MSYS2 shell
* Update pacman mirrors "pacman -Sy && pacman -S pacman-mirrors"
* Install Ninja with "pacman -S mingw-w64-x86_64-ninja"
* Install CMake with "pacman -S mingw-w64-x86_64-cmake"
* Install Qt5 with "pacman -S mingw-w64-x86_64-qt5"
* Install Boost with "pacman -S mingw-w64-x86_64-boost"

## Other Install
* Googletest 1.7 source extracted to [gtest.src]
* Cryptopp source extracted to [cryptopp.src]
* RaiBlocks source source in [rai.src]

## Build Googletest
* Inside directory [gtest.build]
* Run "[cmake]/bin/cmake -G "Unix Makefiles" [gtest.src]"
* Run "make"

## Build cryptopp
* Inside directory [cryptopp.src]
* Run "make CXXFLAGS=-DCRYPTOPP_DISABLE_AESNI static"
* Run "make install PREFIX=[cryptopp]"

## Build RaiBlocks
* Inside directory [rai.build]
* Run "../cmake-3.0.2/bin/cmake -G "Unix Makefiles" -D GTEST_INCLUDE_DIR:PATH=../gtest-1.7.0.src/include -D GTEST_LIBRARY:FILEPATH=/c/Users/colin/gtest-1.7.0.build/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/c/Users/colin/gtest-1.7.0.build/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../rai.src -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final.src -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp562 -D BOOST_ROOT:PATH=../boost_1_56_0 -D Qt5_DIR=/c/Qt/5.3/mingw482_32/lib/cmake/Qt5 ../rai.src"

## Building a package
cpack -G "ZIP"