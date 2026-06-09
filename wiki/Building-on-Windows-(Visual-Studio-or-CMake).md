# Building BodySlide and Outfit Studio on Windows

This page is for developers building BodySlide and Outfit Studio from source on Windows. For Linux, see [Building on Linux](https://github.com/ousnius/BodySlide-and-Outfit-Studio/wiki/Building-on-Linux).

## Recommended toolchain

The actively exercised Windows CI configuration currently uses:

- Visual Studio 18 2026 on `x64`
- CMake 3.16 or newer
- `vcpkg` for third-party dependencies
- Static runtime and static wxWidgets packages

Earlier MSVC versions may still work, but the configuration above is what the project currently builds and tests in CI.

## Preferred: CMake + vcpkg

This is the easiest way to match the current Windows CI setup.

### Prerequisites

- Visual Studio with C++ desktop development tools installed
- CMake 3.16 or newer
- Git

### Bootstrap vcpkg

```powershell
git clone https://github.com/microsoft/vcpkg.git
.\vcpkg\bootstrap-vcpkg.bat -disableMetrics
```

### Install dependencies

Use the same packages as CI:

```powershell
.\vcpkg\vcpkg.exe install wxwidgets[debug-support]:x64-windows-static catch2:x64-windows-static
```

With this setup you do **not** need to manually copy OpenGL headers into the Windows SDK.

### Configure the project

From the repository root:

```powershell
$toolchain = "C:\path\to\vcpkg\scripts\buildsystems\vcpkg.cmake"

cmake -S . -B build\windows-x64-relwithdebinfo `
  -G "Visual Studio 18 2026" `
  -A x64 `
  -DCMAKE_TOOLCHAIN_FILE="$toolchain" `
  -DVCPKG_TARGET_TRIPLET=x64-windows-static `
  -DBSOS_ENABLE_FBXSDK=OFF
```

Useful optional flags:

- `-DBSOS_BUILD_TESTS=ON` to build the Catch2 test target
- `-DBSOS_ENABLE_FBXSDK=OFF` to disable Autodesk FBX SDK integration explicitly

The project defaults to a static MSVC runtime when `CMAKE_MSVC_RUNTIME_LIBRARY` is not set.

### Build

```powershell
cmake --build build\windows-x64-relwithdebinfo --config RelWithDebInfo --target BodySlide OutfitStudio --parallel
```

If you enabled tests:

```powershell
cmake --build build\windows-x64-relwithdebinfo --config RelWithDebInfo --target BSOSTests --parallel
ctest --test-dir build\windows-x64-relwithdebinfo -C RelWithDebInfo --output-on-failure
```

For a fuller overview of the `BSOSTests` target and optional fixture setup, see [Running Tests](https://github.com/ousnius/BodySlide-and-Outfit-Studio/wiki/Running-Tests).

## Using Visual Studio after CMake configure

If you prefer the Visual Studio IDE, configure the project with CMake first and then open the generated solution from the build directory.

For example, after the configure step above, open the generated solution in:

```text
build\windows-x64-relwithdebinfo\BSOS.slnx
```

You can then build `BodySlide`, `OutfitStudio`, and optionally `BSOSTests` from Visual Studio.

## Alternative: existing wxWidgets installation

If you are **not** using `vcpkg`, CMake can also consume an existing wxWidgets build or installation.

Configure CMake with the wxWidgets root directory:

```powershell
cmake -S . -B build\windows-x64-relwithdebinfo `
  -G "Visual Studio 18 2026" `
  -A x64 `
  -DwxWidgets_ROOT_DIR="C:\path\to\wxWidgets"
```

On Windows, the CMake project will automatically derive `wxWidgets_LIB_DIR` from `wxWidgets_ROOT_DIR` when needed.

If you maintain wxWidgets manually, make sure:

- the compiler matches the one used for BodySlide and Outfit Studio
- the architecture matches your target (`x64` vs `Win32`)
- the build configuration is compatible with the runtime you expect to use

`vcpkg` is still the preferred path because it avoids most manual wxWidgets and OpenGL setup issues.

## FBX SDK support

FBX support is optional and only affects Outfit Studio's FBX import/export features.

Current CI builds disable it with `-DBSOS_ENABLE_FBXSDK=OFF`.

If you want FBX support locally, install the [Autodesk FBX SDK](https://aps.autodesk.com/developer/overview/fbx-sdk) and point CMake to it with one of these:

- `-DBSOS_FBXSDK_ROOT=C:\path\to\fbxsdk`
- `-Dfbxsdk_dir=C:\path\to\fbxsdk`
- `FBXSDK_ROOT` environment variable

If the SDK is not found, disable FBX support explicitly and continue the build without it.

## Build outputs and local packaging

At minimum, a usable local build needs:

- `BodySlide.exe`
- `OutfitStudio.exe`
- `res\`
- `lang\`

For packaged builds, also include the XML/config files that ship with the app, such as:

- `BodySlide.xml`
- `BuildSelection.xml`
- `Config.xml`
- `OutfitStudio.xml`
- `RefTemplates.xml`

The Windows CI package also creates empty content folders such as `SliderSets`, `Automations`, `PoseData`, `RefTemplates`, `ShapeData`, `SliderCategories`, `SliderGroups`, and `SliderPresets`.

## Troubleshooting

### CMake cannot find wxWidgets

Use the `vcpkg` toolchain file, or provide `wxWidgets_ROOT_DIR` when using a manual installation.

### CMake cannot find the FBX SDK

Either point CMake at the SDK with `BSOS_FBXSDK_ROOT` or disable FBX support with `-DBSOS_ENABLE_FBXSDK=OFF`.

### Tests fail to configure on Windows

Make sure `Catch2` is installed for the same triplet as the rest of the build, for example `x64-windows-static` when following the CI-style setup.