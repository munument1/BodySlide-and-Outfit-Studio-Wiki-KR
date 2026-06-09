# Running Tests

This page describes the current automated test setup for BodySlide and Outfit Studio.

## Overview

The top-level CMake build exposes an optional Catch2-based test target named `BSOSTests`.

Tests are disabled by default. Enable them by configuring CMake with:

```text
-DBSOS_BUILD_TESTS=ON
```

The current top-level test target covers the Starfield material parsing and database helpers.

## Requirements

- CMake 3.16 or newer
- Catch2 3.x available to CMake
- A build tree configured with `BSOS_BUILD_TESTS=ON`

If you already configured the project without tests, rerun CMake with `BSOS_BUILD_TESTS=ON` before trying to build or run `BSOSTests`.

## Windows example

Using the same `vcpkg`-based dependency flow as the Windows CI build:

```powershell
.\vcpkg\vcpkg.exe install catch2:x64-windows-static wxwidgets[debug-support]:x64-windows-static

$toolchain = "C:\path\to\vcpkg\scripts\buildsystems\vcpkg.cmake"

cmake -S . -B build\windows-x64-relwithdebinfo `
  -G "Visual Studio 18 2026" `
  -A x64 `
  -DCMAKE_TOOLCHAIN_FILE="$toolchain" `
  -DVCPKG_TARGET_TRIPLET=x64-windows-static `
  -DBSOS_BUILD_TESTS=ON `
  -DBSOS_ENABLE_FBXSDK=OFF

cmake --build build\windows-x64-relwithdebinfo --config RelWithDebInfo --target BSOSTests --parallel
ctest --test-dir build\windows-x64-relwithdebinfo -C RelWithDebInfo --output-on-failure
```

## Linux example

On Ubuntu, install the same core test dependency used in CI:

```sh
sudo apt install catch2
```

Then configure and run tests:

```sh
cmake -S . -B build/ubuntu-gcc-relwithdebinfo \
  -G Ninja \
  -DCMAKE_BUILD_TYPE=RelWithDebInfo \
  -DBSOS_BUILD_TESTS=ON \
  -DBSOS_ENABLE_FBXSDK=OFF

cmake --build build/ubuntu-gcc-relwithdebinfo --target BSOSTests --parallel
ctest --test-dir build/ubuntu-gcc-relwithdebinfo --output-on-failure
```

## What CMake enables

When `BSOS_BUILD_TESTS=ON` is enabled, the build does the following:

- finds Catch2 3.x
- enables CTest
- builds the `BSOSTests` executable
- registers discovered Catch2 tests with `catch_discover_tests(...)`

## Optional Starfield material fixture

One test uses an optional real-data fixture controlled by the `SF_MATERIAL_CDB_FIXTURE` environment variable.

If the variable is not set, that fixture-backed test is skipped automatically. This is normal and does not mean the rest of the test suite failed.

Example on Windows PowerShell:

```powershell
$env:SF_MATERIAL_CDB_FIXTURE = "D:\path\to\materials.cdb"
ctest --test-dir build\windows-x64-relwithdebinfo -C RelWithDebInfo --output-on-failure
```

Example on Linux:

```sh
export SF_MATERIAL_CDB_FIXTURE=/path/to/materials.cdb
ctest --test-dir build/ubuntu-gcc-relwithdebinfo --output-on-failure
```

## Troubleshooting

### CMake says Catch2 was not found

Install Catch2 for the same toolchain and architecture as the rest of the build, then rerun CMake.

### No tests are discovered

Make sure the build directory was configured with `BSOS_BUILD_TESTS=ON`. If not, rerun CMake and rebuild `BSOSTests`.

### One test shows as skipped

Check whether `SF_MATERIAL_CDB_FIXTURE` is unset. That specific fixture-backed test is optional.