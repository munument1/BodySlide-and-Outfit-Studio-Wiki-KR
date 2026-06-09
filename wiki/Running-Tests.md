# 테스트 실행

이 페이지는 BodySlide와 Outfit Studio의 현재 자동화된 테스트 설정에 대해 설명합니다.

## 개요

최상위 CMake 빌드는 `BSOSTests`라는 이름의 Catch2 기반 테스트 타겟을 선택적으로 노출합니다.

테스트는 기본적으로 비활성화되어 있습니다. 활성화하려면 다음과 같이 CMake를 구성하세요:

```text
-DBSOS_BUILD_TESTS=ON
```

현재 최상위 테스트 타겟은 스타필드(Starfield) 재질 파싱 및 데이터베이스 헬퍼 기능을 다룹니다.

## 요구 사양

- CMake 3.16 이상
- CMake에서 사용 가능한 Catch2 3.x
- `BSOS_BUILD_TESTS=ON`으로 구성된 빌드 트리

이미 테스트 없이 프로젝트를 구성했다면, `BSOSTests`를 빌드하거나 실행하기 전에 `BSOS_BUILD_TESTS=ON`을 포함하여 CMake를 다시 실행하세요.

## Windows 예시

Windows CI 빌드와 동일한 `vcpkg` 기반 의존성 흐름을 사용하는 경우:

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

## Linux 예시

Ubuntu에서 CI와 동일한 핵심 테스트 의존성 패키지를 설치합니다:

```sh
sudo apt install catch2
```

그다음 테스트를 구성하고 실행합니다:

```sh
cmake -S . -B build/ubuntu-gcc-relwithdebinfo \
  -G Ninja \
  -DCMAKE_BUILD_TYPE=RelWithDebInfo \
  -DBSOS_BUILD_TESTS=ON \
  -DBSOS_ENABLE_FBXSDK=OFF

cmake --build build/ubuntu-gcc-relwithdebinfo --target BSOSTests --parallel
ctest --test-dir build/ubuntu-gcc-relwithdebinfo --output-on-failure
```

## CMake 활성화 항목

`BSOS_BUILD_TESTS=ON`이 활성화되면 빌드 시스템은 다음을 수행합니다:

- Catch2 3.x를 찾습니다.
- CTest를 활성화합니다.
- `BSOSTests` 실행 파일을 빌드합니다.
- `catch_discover_tests(...)`를 통해 발견된 Catch2 테스트들을 등록합니다.

## 선택적 스타필드 재질 픽스처 (Fixture)

한 가지 테스트는 `SF_MATERIAL_CDB_FIXTURE` 환경 변수로 제어되는 선택적인 실제 데이터 픽스처를 사용합니다.

이 변수가 설정되지 않으면 해당 픽스처 기반 테스트는 자동으로 건너뜁니다. 이는 정상적인 동작이며 나머지 테스트 스위트가 실패했다는 의미는 아닙니다.

Windows PowerShell 예시:

```powershell
$env:SF_MATERIAL_CDB_FIXTURE = "D:\path\to\materials.cdb"
ctest --test-dir build\windows-x64-relwithdebinfo -C RelWithDebInfo --output-on-failure
```

Linux 예시:

```sh
export SF_MATERIAL_CDB_FIXTURE=/path/to/materials.cdb
ctest --test-dir build/ubuntu-gcc-relwithdebinfo --output-on-failure
```

## 문제 해결

### CMake가 Catch2를 찾지 못함

빌드의 나머지 부분과 동일한 툴체인 및 아키텍처용 Catch2를 설치한 뒤 CMake를 다시 실행하세요.

### 테스트가 발견되지 않음

빌드 디렉터리가 `BSOS_BUILD_TESTS=ON`으로 구성되었는지 확인하세요. 그렇지 않다면 CMake를 다시 실행하고 `BSOSTests`를 다시 빌드하세요.

### 테스트 하나가 건너뛰어짐(skipped)으로 표시됨

`SF_MATERIAL_CDB_FIXTURE` 환경 변수가 설정되지 않았는지 확인하세요. 해당 특정 픽스처 기반 테스트는 선택 사항입니다.
