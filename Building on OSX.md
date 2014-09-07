# Building on OSX
* Open a terminal and run g++ --version to verify or start the g++ installer

## Other Install
* CMake 3.0.1 installed
* Boost 1.55 extracted to <boost.src>
* Googletest 1.7 extracted to <gtest.src>
* LevelDB extracted to <leveldb.src>
* mu_coin source in <mu_coin_source>

## Build Boost
* Run "./bootstrap.sh --prefix=<boost>
* Run "./b2"
* Run "./b2 install"

