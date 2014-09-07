# Building on OSX
* Install XCode from the AppStore.  XCode command line tools only is insufficient

## Required source
* Boost 1.55 extracted to <boost.src>
* Googletest 1.7 extracted to <gtest.src>
* LevelDB extracted to <leveldb.src>
* mu_coin source in <mu_coin_source>

## Build cmake
* Inside <cmake.build>
* Run "<cmake.src>/configure --prefix=<cmake>"
* Run "make"
* Run "make install"

## Build Boost
* Inside <boost.src>
* Run "./bootstrap.sh --prefix=<boost>
* Run "./b2"
* Run "./b2 install"

## Build leveldb
* Inside <leveldb.src>
* Run "make"

## Build Googletest
* Inside directory <gtest.build>
* Run "<gtest.src>/configure"
* Run "make"

Build cryptopp
* Inside directory <cryptopp.src>
* Run "make"

Build mu_coin
* Inside directory <mu_coin.build>
* Run "<cmake>/bin/cmake -G "Unix Makefiles" -D GTEST_INCLUDE_DIR:PATH=<gtest.src>/include -D GTEST_LIBRARY:FILEPATH=<gtest.src>/libgtest.a -D GTEST_MAIN_LIBRARY:FILEPATH=../gtest-1.7.0.src/libgtest_main.a -D CMAKE_MODULE_PATH:PATH=../mu_coin -D cppnetlib_DIR:PATH=../cpp-netlib-0.11.0-final.src -D CRYPTOPP_ROOT_DIR:PATH=../cryptopp562.src -D CRYPTOPP_INCLUDE_DIR=../cryptopp562.src -D LevelDB_LIBRARY:FILEPATH=../leveldb-1.15.0.src/libleveldb.a -D LevelDB_INCLUDE_PATH:PATH=../leveldb-1.15.0.src/include -D BOOST_ROOT:PATH=../boost_1_56 ../mu_coin