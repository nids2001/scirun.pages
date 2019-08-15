---
title: Build
category: info
tags: build
---

<link rel="stylesheet" href="css/modest.css">

## Platform Notes

**At least C++11 64-bit compiler support is required.**

### Build requirements

#### OS X
  - Tested on 10.10 - 10.13
  - Apple clang 7.2 or newer
  - Qt 4.8
    + Download [Qt 4.8 DMG](http://releases.qt-project.org/qt4/source/qt-mac-opensource-4.8.4.dmg).
    + The above dmg will not work if using OS X 10.11. In this case Qt 4.8 can be acquired through macports using the command 'sudo port install qt4-mac' - more on macports here: https://www.macports.org/install.php
    + Qt 4.8 can also be installed with homebrew.  The instructions are found [here](https://github.com/cartr/homebrew-qt4).

#### Windows
  - Tested on Windows 7-10
  - Visual Studio 2013 & 2017
  - Qt 4.8 or Qt 5.12
    + Build from source, but be sure to download the [Qt 4.8 source archive](http://releases.qt-project.org/qt4/source/qt-everywhere-opensource-src-4.8.4.tar.gz) and build in ***64-bit mode***.
    + [Download](https://www.qt.io) and run the Qt 5 installer.  Only 5.12 needs to be installed.  Make sure to turn off other system versions to save space and build time.


#### Linux
  - Tested on Ubuntu 14.04 LTS, OpenSUSE Leap 42.1
  - gcc 4.8
  - Qt 4.8
    + Build from the [Qt 4.8 source archive](http://releases.qt-project.org/qt4/source/qt-everywhere-opensource-src-4.8.4.tar.gz) , or use system libraries if available.

#### All Platforms
  - [CMake](https://cmake.org/) (platform independent configuring system that is used for generating Makefiles, Visual Studio project files, or Xcode project files)
    + Tested with 2.8 - 3.4
    + Root cmake file is Superbuild/CMakeLists.txt.
    + Building in source directories is not permitted.
    + Make sure BUILD_SHARED_LIBS is on (default setting).

### CMake Build Generators
* Windows
  - Visual Studio 2013 & 2017
* OS X
  - Unix Makefiles
  - Xcode
* Linux
  - Unix Makefiles

## Compiling SCIRun

Run CMake from your build (bin or other build directory of your choice) directory and give a path to the CMake Superbuild directory containing the master CMakeLists.txt file.
For example, on the command line if building from the default SCIRun bin directory:

```
cd bin
cmake ../Superbuild
```

The console version `ccmake`, or GUI version can also be used.
You may be prompted to specify your location of the Qt installation.
If you installed Qt in the default location, it should find Qt automatically.
After configuration is done, generate the make files or project files for your favorite
development environment and build.

Following the previous example, the SCIRun application will be built in bin/SCIRun.

A bash build script (`build.sh`) is also available for Linux and Mac OS X to simplify the process.
Usage information is available using the ***--help*** flag:

```
./build.sh --help
```

## Tagging Releases
On an OSX system, run script `release.sh` in the `src` directory with the release name in format ***beta.XX*** as a parameter.
