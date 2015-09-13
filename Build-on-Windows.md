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

## Building a package
cpack -G "ZIP"