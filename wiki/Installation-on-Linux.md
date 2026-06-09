# Installing BodySlide and Outfit Studio on Linux

This page is for end users installing an existing Linux build of BodySlide and Outfit Studio. If you want to build from source, see [Building BodySlide and Outfit Studio on Linux](https://github.com/ousnius/BodySlide-and-Outfit-Studio/wiki/Building-on-Linux).

## Install runtime dependencies

BodySlide and Outfit Studio need wxWidgets 3.2 or newer, the wxWidgets OpenGL runtime, and GLEW.

On Ubuntu 24.04, the runtime packages are:

```sh
sudo apt install libwxgtk3.2-1t64
sudo apt install libwxgtk-gl3.2-1t64
sudo apt install libglew2.0
```

Package names vary by distribution. If your package manager uses different names, look for the wxWidgets 3.2 GTK runtime, wxWidgets GL runtime, and GLEW runtime packages.

## Install the build

A Linux build should include these program files:

- `BodySlide`
- `OutfitStudio`
- `res/`

Copy `BodySlide`, `OutfitStudio`, and the entire `res` directory into the BodySlide directory in your game or modding setup. Keep `res` in the same directory as the executables.

The `res` directory contains required program data such as XRC files, icons, shaders, and images. BodySlide and Outfit Studio search for `res` next to the executables by default, so the programs will not start correctly if only the executables are copied.

## Mark the executables as runnable

If the files are not already marked executable, run this from the BodySlide directory:

```sh
chmod +x BodySlide OutfitStudio
```

## Start the programs

From the BodySlide directory:

```sh
./BodySlide
./OutfitStudio
```

If either program fails to start because a shared library is missing, install the matching runtime package for your distribution and try again.