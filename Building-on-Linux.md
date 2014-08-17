# Building on Linux

## Packages
* cmake
* libboost1.55-all-dev
* libgtest-dev
* libcrypto++-dev
* libdb6.0++-dev
* qt5-default
* cppnetlib

## Build Googletest
* Run "mkdir gtest-build"
* Inside gtest-build run "cmake -G "Unix Makefiles" /usr/src/gtest
* Then run "make"

## Build cppnetlib
* In the cppnetlib directory run 'cmake -G "Unix Makefiles"'
* Then run "make"

## Build mu_coin
* Run "mkdir mu_coin_build"
* Inside mu_coin_build run "cmake -G "Unix Makefiles" -D GTEST_LIBRARY:FILEPATH=../gtest-build/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=../gtest-build/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../mu_coin -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final ../mu_coin"