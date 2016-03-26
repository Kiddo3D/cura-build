# kiddo-build

This repository contains build scripts used to build SmartControl, Cura and all depenencies from scratch.

## OS X

1. Install CMake (available via [homebrew](http://brew.sh/) or [cmake.org](http://www.cmake.org/))
2. Install latest version of Xcode.
3. On Mac OS X > 10.10, execute command: *brew link openssl --force*
4. Because Fortran is necessary: *brew install gcc*
5. Run these commands:
```shell
git clone https://github.com/Kiddo3D/kiddo-build
cd cura-build
mkdir build
cd build
cmake ..
make
```

## Windows

On Windows, the following dependencies are needed for building:

* CMake (http://www.cmake.org/)
* MinGW-W64 >= 4.9.04 (http://mingw-w64.org/doku.php)
* Python 3.4 (http://python.org/, note that using Python 3.5 is currently untested on Windows)
* PyQt 5.5.1 (https://riverbankcomputing.com/software/pyqt/download5)
* pip install numpy (wheel: numpy-1.10.2+vanilla-cp34-none - http://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) 
* pip install scipy (wheel: scipy-0.17.0rc1-cp34-none - http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy)
* pip install py2exe
* For creating installer we use NSIS 3: http://nsis.sourceforge.net/Main_Page (add to path)
* copy arduino and vcredist to kiddo-build before make package

For 64-bit builds:
* Install protobuf.wheel found in cura-build-binaries (TODO: create cura-build-binaries repo)
* Create empty __init__.py in c:\Python34\Lib\site-packages\google (TODO: make it part of the proto.wheel installation)

```shell
REM 32-bit
git clone https://github.com/Kiddo3D/kiddo-build
cd kiddo-build
mkdir build
cd build
..\env_win32.bat
cmake -G "MinGW Makefiles" ..
mingw32-make package
```

```shell
REM 64-bit
git clone https://github.com/Kiddo3D/kiddo-build
cd kiddo-build
mkdir build
cd build
..\env_win64.bat
cmake -G "MinGW Makefiles" -DBUILD_64BIT:BOOL=ON ..
mingw32-make
mingw32-make package
```

## Ubuntu/Linux

Dependencies:

* python3 (>= 3.4.0)
* python3-dev (>= 3.4.0)
* python3-pyqt5 (>= 5.4.0)
* python3-pyqt5.qtopengl (>= 5.4.0)
* python3-pyqt5.qtquick (>= 5.4.0)
* python3-pyqt5.qtsvg (>= 5.4.0)
* python3-numpy (>= 1.8.0)
* python3-serial (>= 2.6)
* python3-opengl (>= 3.0)
* python3-setuptools
* python3-dev
* qml-module-qtquick2 (>= 5.4.0)
* qml-module-qtquick-window2 (>= 5.4.0)
* qml-module-qtquick-layouts (>= 5.4.0)
* qml-module-qtquick-dialogs (>= 5.4.0)
* qml-module-qtquick-controls (>= 5.4.0)
* zlib1g
* build-essential
* cmake

To build, make sure these dependencies are installed, then clone this repository and run the following commands from your clone:

```shell
sudo apt-get install python3 python3-dev python3-pyqt5 python3-pyqt5.qtopengl python3-pyqt5.qtquick python3-pyqt5.qtsvg python3-numpy python3-serial python3-opengl qml-module-qtquick2 qml-module-qtquick-window2 qml-module-qtquick-layouts qml-module-qtquick-dialogs qml-module-qtquick-controls
git clone https://github.com/Kiddo3D/kiddo-build
cd cura-build
mkdir build
cd build
cmake ..
make
make package
```
