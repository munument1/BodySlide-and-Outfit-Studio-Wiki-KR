# Windows에서 BodySlide와 Outfit Studio 빌드하기

이 페이지는 Windows에서 소스 코드를 통해 BodySlide와 Outfit Studio를 직접 빌드하려는 개발자를 위한 문서입니다. Linux의 경우 [Linux에서 빌드하기](Building-on-Linux.md) 문서를 참고하세요.

## 권장 툴체인 (Toolchain)

현재 활발히 사용되는 Windows CI 설정은 다음과 같습니다:

- Visual Studio 18 2026 (`x64`)
- CMake 3.16 이상
- 서드파티 의존성 관리를 위한 `vcpkg`
- 정적 런타임(Static runtime) 및 정적 wxWidgets 패키지

이전 버전의 MSVC도 작동할 수 있지만, 위 설정이 현재 프로젝트가 CI에서 빌드하고 테스트하는 환경입니다.

## 권장 방법: CMake + vcpkg

현재 Windows CI 설정과 동일하게 맞추는 가장 쉬운 방법입니다.

### 사전 준비 사항

- C++ 데스크톱 개발 도구가 설치된 Visual Studio
- CMake 3.16 이상
- Git

### vcpkg 부트스트랩 (Bootstrap)

```powershell
git clone https://github.com/microsoft/vcpkg.git
.\vcpkg\bootstrap-vcpkg.bat -disableMetrics
```

### 의존성 패키지 설치

CI와 동일한 패키지들을 설치합니다:

```powershell
.\vcpkg\vcpkg.exe install wxwidgets[debug-support]:x64-windows-static catch2:x64-windows-static
```

이 설정을 사용하면 OpenGL 헤더를 Windows SDK에 수동으로 복사할 필요가 **없습니다**.

### 프로젝트 구성 (Configure)

저장소 루트 디렉터리에서 다음을 실행합니다:

```powershell
$toolchain = "C:\path\to\vcpkg\scripts\buildsystems\vcpkg.cmake"

cmake -S . -B build\windows-x64-relwithdebinfo `
  -G "Visual Studio 18 2026" `
  -A x64 `
  -DCMAKE_TOOLCHAIN_FILE="$toolchain" `
  -DVCPKG_TARGET_TRIPLET=x64-windows-static `
  -DBSOS_ENABLE_FBXSDK=OFF
```

유용한 선택적 플래그:

- Catch2 테스트 타겟을 빌드하려면 `-DBSOS_BUILD_TESTS=ON` 추가
- Autodesk FBX SDK 통합을 명시적으로 비활성화하려면 `-DBSOS_ENABLE_FBXSDK=OFF` 추가

`CMAKE_MSVC_RUNTIME_LIBRARY`가 설정되지 않은 경우, 프로젝트는 기본적으로 정적 MSVC 런타임을 사용합니다.

### 빌드 (Build)

```powershell
cmake --build build\windows-x64-relwithdebinfo --config RelWithDebInfo --target BodySlide OutfitStudio --parallel
```

테스트를 활성화한 경우:

```powershell
cmake --build build\windows-x64-relwithdebinfo --config RelWithDebInfo --target BSOSTests --parallel
ctest --test-dir build\windows-x64-relwithdebinfo -C RelWithDebInfo --output-on-failure
```

`BSOSTests` 타겟 및 선택적 픽스처(fixture) 설정에 대한 자세한 내용은 [테스트 실행](Running-Tests.md) 문서를 참고하세요.

## CMake 구성 후 Visual Studio 사용하기

Visual Studio IDE 사용을 선호한다면, 먼저 CMake로 프로젝트를 구성한 다음 빌드 디렉터리에 생성된 솔루션 파일을 엽니다.

예를 들어 위 구성을 마친 후, 다음 위치의 솔루션 파일을 엽니다:

```text
build\windows-x64-relwithdebinfo\BSOS.slnx
```

그다음 Visual Studio에서 `BodySlide`, `OutfitStudio`, 그리고 선택적으로 `BSOSTests`를 빌드할 수 있습니다.

## 대안: 기존 wxWidgets 설치본 사용하기

`vcpkg`를 사용하지 **않는** 경우, CMake는 기존에 빌드되거나 설치된 wxWidgets를 사용할 수 있습니다.

wxWidgets 루트 디렉터리를 지정하여 CMake를 구성합니다:

```powershell
cmake -S . -B build\windows-x64-relwithdebinfo `
  -G "Visual Studio 18 2026" `
  -A x64 `
  -DwxWidgets_ROOT_DIR="C:\path\to\wxWidgets"
```

Windows의 경우, 필요한 경우 CMake 프로젝트가 `wxWidgets_ROOT_DIR`로부터 `wxWidgets_LIB_DIR`을 자동으로 도출합니다.

wxWidgets를 수동으로 관리하는 경우 다음 사항을 확인하세요:

- 컴파일러가 BodySlide 및 Outfit Studio와 빌드 시 사용한 것과 일치해야 함
- 아키텍처가 타겟(`x64` 또는 `Win32`)과 일치해야 함
- 빌드 구성이 사용하려는 런타임과 호환되어야 함

대부분의 수동 wxWidgets 및 OpenGL 설정 문제를 피할 수 있으므로 `vcpkg` 사용을 여전히 권장합니다.

## FBX SDK 지원

FBX 지원은 선택 사항이며 Outfit Studio의 FBX 임포트/익스포트 기능에만 영향을 줍니다.

현재 CI 빌드에서는 `-DBSOS_ENABLE_FBXSDK=OFF`를 사용하여 비활성화하고 있습니다.

로컬에서 FBX 지원이 필요하다면 [Autodesk FBX SDK](https://aps.autodesk.com/developer/overview/fbx-sdk)를 설치하고 다음 중 하나를 사용하여 CMake에 경로를 지정하세요:

- `-DBSOS_FBXSDK_ROOT=C:\path\to\fbxsdk`
- `-Dfbxsdk_dir=C:\path\to\fbxsdk`
- `FBXSDK_ROOT` 환경 변수

SDK를 찾을 수 없다면 FBX 지원을 명시적으로 비활성화하고 빌드를 계속 진행하세요.

## 빌드 출력물 및 로컬 패키징

최소한 다음 파일들이 있어야 로컬에서 빌드한 결과물을 사용할 수 있습니다:

- `BodySlide.exe`
- `OutfitStudio.exe`
- `res\`
- `lang\`

패키징된 빌드의 경우 프로그램과 함께 제공되는 다음과 같은 XML/구성 파일들도 포함하세요:

- `BodySlide.xml`
- `BuildSelection.xml`
- `Config.xml`
- `OutfitStudio.xml`
- `RefTemplates.xml`

Windows CI 패키지는 `SliderSets`, `Automations`, `PoseData`, `RefTemplates`, `ShapeData`, `SliderCategories`, `SliderGroups`, `SliderPresets`와 같은 빈 콘텐츠 폴더들도 함께 생성합니다.

## 문제 해결

### CMake가 wxWidgets를 찾지 못함

`vcpkg` 툴체인 파일을 사용하거나, 수동 설치본을 사용하는 경우 `wxWidgets_ROOT_DIR`을 제공하세요.

### CMake가 FBX SDK를 찾지 못함

`BSOS_FBXSDK_ROOT`로 SDK 경로를 지정하거나 `-DBSOS_ENABLE_FBXSDK=OFF`로 FBX 지원을 비활성화하세요.

### Windows에서 테스트 구성(configure)이 실패함

빌드의 나머지 부분과 동일한 트리플렛(triplet)으로 `Catch2`가 설치되었는지 확인하세요. 예를 들어 CI 스타일 설정을 따르는 경우 `x64-windows-static`이어야 합니다.
