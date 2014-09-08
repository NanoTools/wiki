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
* CMake 3.0.1 extracted to <cmake.src>
* Boost 1.55 extracted to <boost.src>
* Googletest 1.7 extracted to <gtest.src>
* LevelDB (zalanyib/leveldb-mingw) extracted to <leveldb.src>
* Cryptopp extracted to <cryptopp.src>
* mu_coin source in <mu_coin.src>

## Run MSYS shell
* Run "c:/MinGW/msys/1.0/msys.bat"
* Run "export PATH=$PATH:/c/MinGW/bin/" inside MSYS shell to add compiler tools to path

## Build cmake
* Inside directory <cmake.build> run "<cmake.src>/configure --prefix=<cmake>"
* Run "make"
* Run "make install"

## Build Boost
* Inside directory <boost.src>
* Run "bootstrap.bat --with-toolset=mingw --prefix=<boost>"
* Edit the file project-config.jam and replace 'mingw' by 'gcc
* Run "./b2"

## Build LevelDB
* Inside directory <leveldb.src>
* Run "make"

## Build Googletest
* Inside directory <gtest.build>
* Run "<gtest.src>/configure"
* Run "make"

Build cryptopp
* Inside directory <cryptopp.src>
* Run "make"

Build qt

it is some bug in MinGW, when one of -ansi, -std=c++11, -std=c++03 and -std=c++98 are used. in file {MinGW dir}/include/io.h replace

__CRT_INLINE off64_t lseek64 (int, off64_t, int);
__CRT_INLINE off64_t lseek64 (int fd, off64_t offset, int whence) {
with

__CRT_INLINE _off64_t lseek64 (int, _off64_t, int);
__CRT_INLINE _off64_t lseek64 (int fd, _off64_t offset, int whence) {

