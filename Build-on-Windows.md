# Building on Windows

## MinGW
* Download MinGW
* Inside MinGW Installation Manager install -> Basic Setup
* Right click "mingw32-base bin" -> Mark For Installation
* Right click "mingw32-gcc-g++ bin" -> Mark For Installation
* Right click "msys-base bin" -> Mark For Installation
* Installation -> Apply All Changes

## Other Install
* CMake 3.0.1
* mu_coin source in <mu_coin_source>

## Set up CMake
* Run cmake-gui
* Set "Where is the Source Code" to <mu_coin_source>
* Set "Where to build the binaries" to <mu_coin_build> which should not be inside <mu_coin_source>
* Push "Configure"
* When asked "Build directory does not exist, should I create it" push "Yes"
* Under "Specify the generator for this project, select "MinGW Makefiles"
* Select "Use default native compilers"
* Push "Finish"