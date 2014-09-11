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
* Run "./b2 --without-context --without-coroutine --build-dir=[boost.build] --prefix=[boost] link=static install"

## Build LevelDB
* Inside directory [leveldb.src]
* Edit build_detect_platform add
    MINGW32_NT-6.2)
        PLATFORM=OS_MINGW
        COMMON_FLAGS="$MEMCMP_FLAG -pthread -DOS_MINGW"
        PLATFORM_LDFLAGS="-pthread"
        PORT_FILE=port/port_posix.cc
        ;;
* Edit port/port_posix.h add 
#elif defined(OS_MINGW)
  #define PLATFORM_IS_LITTLE_ENDIAN true
* Run "make"

## Build Googletest
* Inside directory [gtest.build]
* Run "[cmake]/bin/cmake -G "Unix Makefiles" [gtest.src]"
* Run "make"

## Build cryptopp
* Inside directory [cryptopp.src]
* Run "make CXXFLAGS=-DCRYPTOPP_DISABLE_AESNI"
* Run "make install PREFIX=[cryptopp]"

## Build mu_coin
* Inside directory [mu_coin.build]
* Run "../cmake-3.0.1/bin/cmake -G "Unix Makefiles" -D GTEST_INCLUDE_DIR:PATH=../gtest-1.7.0.src/include -D GTEST_LIBRARY:FILEPATH=/c/Users/colin/gtest-1.7.0.build/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/c/Users/colin/gtest-1.7.0.build/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../mu_coin.src -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final.src -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp562 -D LevelDB_LIBRARY:FILEPATH=/c/Users/colin/leveldb.src/libleveldb.a -D LevelDB_INCLUDE_PATH:PATH=../leveldb.src/include -D BOOST_ROOT:PATH=../boost_1_56_0 -D Qt5_DIR=/c/Qt/5.3/mingw482_32/lib/cmake/Qt5 ../mu_coin.src"