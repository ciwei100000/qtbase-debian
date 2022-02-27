# qtbase-debian
This repository is a custom version of https://salsa.debian.org/qt-kde-team/qt/qtbase.git

## Changes

   - Enable Link-Time Code Generation (ltcg) for building the qt packages

## Build

   Go to the root direction of this repository and executes the following commands
   - set up building flags
   ```
   $ export DEB_CFLAGS_APPEND="-O3 -fdevirtualize-at-ltrans -fipa-pta -flto-odr-type-merging -ffat-lto-objects"; \
     export DEB_CXXFLAGS_APPEND="-O3 -fdevirtualize-at-ltrans -fipa-pta -flto-odr-type-merging -ffat-lto-objects"; \
     export DEB_LDFLAGS_APPEND="-O3 --fdevirtualize-at-ltrans -fipa-pta -flto-odr-type-merging -ffat-lto-objects"
   ```
   - install build dependencies*
   ```
   $ mk-build-deps -s sudo -i
   ```
   - start building
   ```
   $ dpkg-buildpackage -b --no-sign -j32
   ```
