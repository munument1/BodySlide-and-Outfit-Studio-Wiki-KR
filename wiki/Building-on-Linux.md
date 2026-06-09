# Building BodySlide and Outfit Studio on Linux

This page is for developers building BodySlide and Outfit Studio from source on Linux. If you already have a Linux build and only want to install it, see [Installation on Linux](https://github.com/ousnius/BodySlide-and-Outfit-Studio/wiki/Installation-on-Linux).

## Build requirements

- CMake 3.16 or newer.
- A C++17 compiler and normal build tools.
- wxWidgets 3.2 or newer, including the OpenGL component.
- OpenGL, GLU, and GLEW development files.
- DirectX-Headers development files.
- Optional: Autodesk FBX SDK for Outfit Studio FBX import/export support.
- Optional: Catch2 3.x if you want to build the `BSOSTests` target.

If you want a CI-like Linux dependency set on Ubuntu, install:

```sh
sudo apt install build-essential cmake directx-headers-dev gcc g++ libglew-dev libgl1-mesa-dev libglu1-mesa-dev libwxgtk3.2-dev ninja-build pkg-config
```

If you want to build the tests as well, add Catch2:

```sh
sudo apt install catch2
```

Package names vary by distribution. The important parts are wxWidgets 3.2 or newer, wxWidgets OpenGL support, GLEW, and the DirectX-Headers package used by the current Linux build.

## wxWidgets notes

If you get errors about an ABI mismatch, wxWidgets was built with a different compiler version than BodySlide and Outfit Studio. Build both with the same compiler.

Either GTK 2 or GTK 3 can work. GTK 2 tends to have more background color problems. GTK 3 can distort some widgets because they do not have enough space.

Some wxWidgets configure options, such as `--enable-universal`, can produce a broken wxWidgets library for this project. Prefer as few wxWidgets build options as possible. Some distribution-provided wxWidgets packages are also broken, so you may need to build wxWidgets yourself.

## Building wxWidgets with CMake

If you build wxWidgets with CMake, install it to a local prefix:

```sh
cmake -S /path/to/wxWidgets -B wx-build -DCMAKE_BUILD_TYPE=Release -DwxBUILD_TOOLKIT=gtk3 -DCMAKE_INSTALL_PREFIX=$HOME/opt/wxwidgets-gtk3
cmake --build wx-build --parallel
cmake --install wx-build
```

Then configure BodySlide and Outfit Studio with that prefix:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DCMAKE_PREFIX_PATH=$HOME/opt/wxwidgets-gtk3
```

The project first looks for an installed wxWidgets CMake package and then falls back to CMake's `FindwxWidgets` module, which uses `wx-config` on Linux.

If CMake still does not find wxWidgets, point it directly at the package directory or root:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DwxWidgets_DIR=$HOME/opt/wxwidgets-gtk3/lib/cmake/wxWidgets
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DwxWidgets_ROOT=$HOME/opt/wxwidgets-gtk3
```

## Building wxWidgets with configure and make

For a wxWidgets build made with `configure` and `make` instead of CMake, pass the `wx-config` path:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DwxWidgets_CONFIG_EXECUTABLE=$HOME/opt/wxwidgets-gtk3/bin/wx-config
```

## Configure and build BodySlide and Outfit Studio

From the repository root:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release
cmake --build Release --parallel
```

To match the Linux CI configuration more closely:

```sh
cmake -S . -B build/ubuntu-gcc-relwithdebinfo \
	-G Ninja \
	-DCMAKE_BUILD_TYPE=RelWithDebInfo \
	-DBSOS_ENABLE_FBXSDK=OFF

cmake --build build/ubuntu-gcc-relwithdebinfo --parallel
```

The possible values for `CMAKE_BUILD_TYPE` are:

- `Release`
- `RelWithDebInfo`
- `Debug`
- `MinSizeRel`
- Empty, for no explicit build type

Useful build options:

```sh
cmake --build Release --verbose
cmake --build Release --parallel 4
```

## Building and running tests

The optional Catch2-based test target is disabled by default.

Enable it during configure:

```sh
cmake -S . -B build/ubuntu-gcc-relwithdebinfo \
	-G Ninja \
	-DCMAKE_BUILD_TYPE=RelWithDebInfo \
	-DBSOS_BUILD_TESTS=ON \
	-DBSOS_ENABLE_FBXSDK=OFF
```

Then build and run the tests:

```sh
cmake --build build/ubuntu-gcc-relwithdebinfo --target BSOSTests --parallel
ctest --test-dir build/ubuntu-gcc-relwithdebinfo --output-on-failure
```

For more details, see [Running Tests](https://github.com/ousnius/BodySlide-and-Outfit-Studio/wiki/Running-Tests).

## Selecting a compiler

Set `CC` and `CXX` before running CMake:

```sh
CC=clang CXX=clang++ cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release
```

The build directory must be empty when you change compilers. Otherwise, CMake keeps using the compiler it found during the first configure. Build wxWidgets with the same compiler; the wxWidgets configure script also uses `CC` and `CXX`.

## FBX SDK support

FBX SDK support is optional. By default, CMake enables FBX support when it can find the SDK and builds Outfit Studio without FBX import/export when it cannot.

To disable FBX support explicitly:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DBSOS_ENABLE_FBXSDK=OFF
```

To enable FBX support from a non-standard location, pass the SDK root with `BSOS_FBXSDK_ROOT`, the legacy `fbxsdk_dir` cache variable, or the `FBXSDK_ROOT` environment variable:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DBSOS_FBXSDK_ROOT=/opt/fbxsdk
```

## Runtime files for local testing

The `BodySlide` and `OutfitStudio` executables must be able to find the `res` directory. It contains required program data such as XRC files, icons, shaders, and images.

By default, the executables look for `res` in the same directory as the executables. When copying a local build into the BodySlide directory inside a game or modding setup, copy the whole `res` directory with the executables.