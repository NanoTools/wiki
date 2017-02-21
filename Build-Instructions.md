## Required source
* Boost 1.62+ extracted to [boost.src]
* (wallet) Qt 5.x open source edition extracted to [qt.src]
* RaiBlocks source in [rai.src]

## Required build tools
* (macOS) XCode >= 7.3
* (Windows) Visual Studio 2015
* (Windows) NSIS package builder
* (*nix) Clang >= 3.5 or GCC >= 5
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

## CMake variables
* BOOST_ROOT [boost]
* CMAKE_BUILD_TYPE Release
* ACTIVE_NETWORK rai_live_network
* Qt5_DIR [qt]lib/cmake/Qt5

## Build RaiBlocks
* Generate with cmake then build with your compiler
* (*nix) to build node without GUI execute: make rai_node
* (*nix) to build wallet with GUI execute: make rai_wallet

## Building a package
* (macOS) cpack -G "DragNDrop"
* (Windows) cpack -G "NSIS"
* (*nix) cpack -G "TBZ2"