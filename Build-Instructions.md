## Required source
* Boost 1.59 extracted to [boost.src]
* Qt 5.x open source edition extracted to [qt.src]
* RaiBlocks source in [rai.src]

## Required build tools
* (macOS) XCode 7.3
* (Windows) Visual Studio 2015
* (Windows) NSIS package builder
* (*nix) Clang 3.5 or GCC 5
* CMake

## Build Boost
* Inside [boost.src]
* Run "./bootstrap.sh
* Run "./b2 --prefix=[boost] --build-dir=[boost.build] link=static install"
* (Windows) An additional b2 option "address-model 64" for x64 builds

## Building Qt
* In [qt.build] execute [qt.src]/configure -shared -opensource -nomake examples -nomake tests -confirm-license  -prefix [qt]
* make
* make install
* (Windows) Use nmake instead of make. 

## Build RaiBlocks
* Inside directory [rai.build]
* Run "../cmake-3.0.1/bin/cmake -G "Unix Makefiles" -D GTEST_INCLUDE_DIR:PATH=../gtest-1.7.0.src/include -D GTEST_LIBRARY:FILEPATH=/Users/colin/Desktop/gtest-1.7.0.build/lib/.libs/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=/Users/colin/Desktop/gtest-1.7.0.build/lib/.libs/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../rai.src -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final.src -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp562 -D BOOST_ROOT=../boost_1_56 -D Qt5_DIR=../../Qt/5.3/clang_64/lib/cmake/Qt5 ../rai.src"

## Building a package
* (macOS) cpack -G "DragNDrop"
* (Windows) cpack -G "NSIS"
* (*nix) cpack -G "TBZ2"