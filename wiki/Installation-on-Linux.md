# Linux에 BodySlide와 Outfit Studio 설치하기

이 페이지는 이미 빌드된 Linux용 BodySlide와 Outfit Studio를 설치하려는 사용자를 위한 문서입니다. 소스 코드를 통해 직접 빌드하려는 경우 [Linux에서 빌드하기](Building-on-Linux.md) 문서를 참고하세요.

## 런타임 의존성 설치

BodySlide와 Outfit Studio를 실행하려면 wxWidgets 3.2 이상, wxWidgets OpenGL 런타임, 그리고 GLEW가 필요합니다.

Ubuntu 24.04의 경우, 런타임 패키지는 다음과 같습니다:

```sh
sudo apt install libwxgtk3.2-1t64
sudo apt install libwxgtk-gl3.2-1t64
sudo apt install libglew2.0
```

패키지 이름은 배포판마다 다를 수 있습니다. 패키지 매니저에서 다른 이름을 사용한다면 wxWidgets 3.2 GTK 런타임, wxWidgets GL 런타임, GLEW 런타임 패키지를 찾아보세요.

## 빌드 파일 설치

Linux 빌드 버전에는 최소한 다음 프로그램 파일들이 포함되어 있어야 합니다:

- `BodySlide`
- `OutfitStudio`
- `res/`

`BodySlide`, `OutfitStudio` 파일과 `res` 디렉터리 전체를 게임이나 모딩 환경 내의 BodySlide 디렉터리에 복사하세요. `res` 디렉터리는 항상 실행 파일과 동일한 위치에 두어야 합니다.

`res` 디렉터리에는 XRC 파일, 아이콘, 셰이더, 이미지 등 프로그램 실행에 필수적인 데이터가 들어 있습니다. BodySlide와 Outfit Studio는 기본적으로 실행 파일 옆에서 `res`를 검색하므로, 실행 파일만 복사하면 프로그램이 정상적으로 실행되지 않습니다.

## 실행 권한 부여

파일에 실행 권한이 부여되어 있지 않다면, BodySlide 디렉터리에서 다음 명령어를 실행하세요:

```sh
chmod +x BodySlide OutfitStudio
```

## 프로그램 실행

BodySlide 디렉터리에서 다음을 실행합니다:

```sh
./BodySlide
./OutfitStudio
```

공유 라이브러리(shared library) 누락으로 프로그램이 실행되지 않는 경우, 해당 배포판에 맞는 런타임 패키지를 설치한 뒤 다시 시도하세요.
