_-- please note: using docker has been recommended as a faster method of installation: https://github.com/nanocurrency/raiblocks/wiki/Docker-node --_
## Required source
* [Boost 1.66](http://www.boost.org/users/history/version_1_66_0.html) extracted to [boost.src] (OR `sh raiblocks/ci/bootstrap_boost.sh`)
* (wallet) [Qt 5.x open source edition](https://www1.qt.io/download-open-source/) extracted to [qt.src]
* RaiBlocks source in [rai.src]

## Required build tools
* (macOS) XCode >= 7.3
* (Windows) Visual Studio 2015
* (Windows) NSIS package builder
* (*nix) Clang >= 3.5 or GCC >= 5
* CMake

## Build Boost 
### Option 1
* Inside `raiblocks` directory
* Run `sh ci/bootstrap_boost.sh`
* This will build Boost at `/usr/local/boost/`
* That's it!
### Option 2
* Inside [boost.src]
* Run `./bootstrap.sh`
* Run `./b2 --prefix=[boost] --build-dir=[boost.build] link=static install`
* (Windows) An additional b2 option `address-model=64` for x64 builds

## Building Qt
* In [qt.build] execute `[qt.src]/configure -shared -opensource -nomake examples -nomake tests -confirm-license  -prefix [qt]`
* `make`
* `make install`
* (Windows) Use `nmake` instead of `make`. 

## CMake variables (`cmake -DVARNAME=VARVALUE`).
* BOOST_ROOT [boost] (`/usr/local/boost/` if bootstrapped)
* _CMAKE_BUILD_TYPE Release_ (default)
* _ACTIVE_NETWORK rai_live_network_ (default)
* Qt5_DIR [qt]lib/cmake/Qt5 (to build GUI wallet)
* RAIBLOCKS_GUI ON (to build GUI wallet)
* ENABLE_AVX2 ON, _optional_ PERMUTE_WITH_GATHER ON, _optional_ PERMUTE_WITH_SHUFFLES ON (for CPU with AXV2 support, choose fastest method for your CPU with https://github.com/sneves/blake2-avx2/)
* CRYPTOPP_CUSTOM ON (more conservative building of Crypto++ for wider range of systems)
* BOOST_CUSTOM ON (use bundled FindBoost.cmake for boost 1.66 on Windows commit 8fd47b20dca0c9fc82c5c4d240432503d6fb11a4+)

## Build RaiBlocks
* `git submodule update --init --recursive`
* Generate with cmake then build with your compiler
* (*nix) to build node without GUI execute: `make rai_node`
* (*nix) to build wallet with GUI execute: `make rai_wallet`

## Building a package
* (macOS) `cpack -G "DragNDrop"`
* (Windows) `cpack -G "NSIS"`
* (*nix) `cpack -G "TBZ2"`

## Testing RaiBlocks
* In order to run the tests, the corresponding CMake variable must be set: `-D RAIBLOCKS_TEST=ON`.
* With this variable set, make will also build test files, and will produce `core_test` and `slow_test` binaries, which can be executed like `./core_test`.
* To run a node on the test network, set CMake variable: -DACTIVE_NETWORK=rai_test_network