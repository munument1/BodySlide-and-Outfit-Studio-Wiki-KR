# Linux에서 BodySlide와 Outfit Studio 빌드하기

이 페이지는 Linux에서 소스 코드를 통해 BodySlide와 Outfit Studio를 직접 빌드하려는 개발자를 위한 문서입니다. 이미 빌드된 Linux용 파일을 설치하려는 경우 [Linux에 설치하기](Installation-on-Linux.md) 문서를 참고하세요.

## 빌드 요구 사양

- CMake 3.16 이상.
- C++17 컴파일러 및 일반적인 빌드 도구.
- wxWidgets 3.2 이상 (OpenGL 컴포넌트 포함).
- OpenGL, GLU, GLEW 개발용 파일.
- DirectX-Headers 개발용 파일.
- 선택 사항: Outfit Studio의 FBX 임포트/익스포트 지원을 위한 Autodesk FBX SDK.
- 선택 사항: `BSOSTests` 타겟을 빌드하려는 경우 Catch2 3.x.

Ubuntu에서 CI(지속적 통합) 환경과 유사한 Linux 의존성 패키지들을 설치하려면 다음 명령어를 실행하세요:

```sh
sudo apt install build-essential cmake directx-headers-dev gcc g++ libglew-dev libgl1-mesa-dev libglu1-mesa-dev libwxgtk3.2-dev ninja-build pkg-config
```

테스트까지 빌드하고 싶다면 Catch2를 추가하세요:

```sh
sudo apt install catch2
```

패키지 이름은 배포판마다 다를 수 있습니다. 중요한 부분은 wxWidgets 3.2 이상, wxWidgets OpenGL 지원, GLEW, 그리고 현재 Linux 빌드에서 사용하는 DirectX-Headers 패키지입니다.

## wxWidgets 참고 사항

ABI 불일치(mismatch)에 관한 오류가 발생한다면, wxWidgets가 BodySlide 및 Outfit Studio와 서로 다른 컴파일러 버전으로 빌드된 것입니다. 두 프로젝트 모두 동일한 컴파일러로 빌드해야 합니다.

GTK 2 또는 GTK 3 모두 작동 가능합니다. GTK 2는 배경색 관련 문제가 더 많이 발생하는 경향이 있습니다. GTK 3는 일부 위젯이 충분한 공간을 확보하지 못해 왜곡될 수 있습니다.

`--enable-universal`과 같은 일부 wxWidgets 구성 옵션은 이 프로젝트에서 제대로 작동하지 않는 wxWidgets 라이브러리를 생성할 수 있습니다. 가능한 한 wxWidgets 빌드 옵션을 최소화하는 것이 좋습니다. 일부 배포판에서 제공하는 wxWidgets 패키지도 문제가 있을 수 있으므로, 필요한 경우 wxWidgets를 직접 빌드해야 할 수도 있습니다.

## CMake로 wxWidgets 빌드하기

CMake를 사용하여 wxWidgets를 빌드하는 경우, 로컬 프리픽스(prefix) 경로에 설치하세요:

```sh
cmake -S /path/to/wxWidgets -B wx-build -DCMAKE_BUILD_TYPE=Release -DwxBUILD_TOOLKIT=gtk3 -DCMAKE_INSTALL_PREFIX=$HOME/opt/wxwidgets-gtk3
cmake --build wx-build --parallel
cmake --install wx-build
```

그다음 해당 프리픽스 경로를 지정하여 BodySlide와 Outfit Studio를 구성합니다:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DCMAKE_PREFIX_PATH=$HOME/opt/wxwidgets-gtk3
```

프로젝트는 먼저 설치된 wxWidgets CMake 패키지를 찾고, 찾지 못하면 Linux의 `wx-config`를 사용하는 CMake의 `FindwxWidgets` 모듈로 대체하여 검색합니다.

CMake가 여전히 wxWidgets를 찾지 못한다면 패키지 디렉터리나 루트를 직접 지정하세요:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DwxWidgets_DIR=$HOME/opt/wxwidgets-gtk3/lib/cmake/wxWidgets
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DwxWidgets_ROOT=$HOME/opt/wxwidgets-gtk3
```

## configure와 make로 wxWidgets 빌드하기

CMake 대신 `configure`와 `make`로 빌드된 wxWidgets를 사용하는 경우, `wx-config` 경로를 전달하세요:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DwxWidgets_CONFIG_EXECUTABLE=$HOME/opt/wxwidgets-gtk3/bin/wx-config
```

## BodySlide와 Outfit Studio 구성 및 빌드

저장소 루트 디렉터리에서 다음을 실행합니다:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release
cmake --build Release --parallel
```

Linux CI 설정과 더 가깝게 맞추려면 다음과 같이 실행하세요:

```sh
cmake -S . -B build/ubuntu-gcc-relwithdebinfo \
	-G Ninja \
	-DCMAKE_BUILD_TYPE=RelWithDebInfo \
	-DBSOS_ENABLE_FBXSDK=OFF

cmake --build build/ubuntu-gcc-relwithdebinfo --parallel
```

`CMAKE_BUILD_TYPE`에 사용할 수 있는 값은 다음과 같습니다:

- `Release`
- `RelWithDebInfo`
- `Debug`
- `MinSizeRel`
- 비워 둠 (명시적인 빌드 유형 없음)

유용한 빌드 옵션:

```sh
cmake --build Release --verbose
cmake --build Release --parallel 4
```

## 테스트 빌드 및 실행

Catch2 기반의 테스트 타겟은 기본적으로 비활성화되어 있습니다.

구성 단계에서 이를 활성화하세요:

```sh
cmake -S . -B build/ubuntu-gcc-relwithdebinfo \
	-G Ninja \
	-DCMAKE_BUILD_TYPE=RelWithDebInfo \
	-DBSOS_BUILD_TESTS=ON \
	-DBSOS_ENABLE_FBXSDK=OFF
```

그다음 테스트를 빌드하고 실행합니다:

```sh
cmake --build build/ubuntu-gcc-relwithdebinfo --target BSOSTests --parallel
ctest --test-dir build/ubuntu-gcc-relwithdebinfo --output-on-failure
```

자세한 내용은 [테스트 실행](Running-Tests.md) 문서를 참고하세요.

## 컴파일러 선택

CMake를 실행하기 전에 `CC`와 `CXX`를 설정하세요:

```sh
CC=clang CXX=clang++ cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release
```

컴파일러를 변경할 때는 빌드 디렉터리가 비어 있어야 합니다. 그렇지 않으면 CMake는 첫 번째 구성 시 발견한 컴파일러를 계속 사용합니다. wxWidgets도 동일한 컴파일러로 빌드해야 하며, wxWidgets의 구성 스크립트 역시 `CC`와 `CXX`를 사용합니다.

## FBX SDK 지원

FBX SDK 지원은 선택 사항입니다. 기본적으로 CMake는 SDK를 찾을 수 있으면 FBX 지원을 활성화하고, 찾을 수 없으면 FBX 임포트/익스포트 기능 없이 Outfit Studio를 빌드합니다.

FBX 지원을 명시적으로 비활성화하려면:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DBSOS_ENABLE_FBXSDK=OFF
```

비표준 위치에 있는 FBX SDK를 사용하려면 `BSOS_FBXSDK_ROOT` 인자나 기존의 `fbxsdk_dir` 캐시 변수, 또는 `FBXSDK_ROOT` 환경 변수를 통해 SDK 루트 경로를 전달하세요:

```sh
cmake -S . -B Release -DCMAKE_BUILD_TYPE=Release -DBSOS_FBXSDK_ROOT=/opt/fbxsdk
```

## 로컬 테스트를 위한 런타임 파일

`BodySlide`와 `OutfitStudio` 실행 파일이 `res` 디렉터리를 찾을 수 있어야 합니다. 이 디렉터리에는 XRC 파일, 아이콘, 셰이더, 이미지 등 프로그램에 필요한 데이터가 들어 있습니다.

기본적으로 실행 파일은 자신과 동일한 디렉터리에서 `res`를 찾습니다. 로컬에서 빌드한 파일을 게임이나 모딩 환경 내의 BodySlide 디렉터리에 복사할 때, 실행 파일과 함께 `res` 디렉터리 전체를 복사해 주세요.
