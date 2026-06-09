## 설치

Nexus Mods의 모드 페이지 중 하나에서 사용하는 모드 매니저로 프로그램을 다운로드하면 됩니다.

수동 설치도 가능하지만, 모드 매니저를 사용하는 것을 권장합니다. 또한 해당 게임용 다운로드 파일에서 제공하는 기본 폴더 구조를 유지하는 것이 좋습니다. 이렇게 해야 애드온을 설치하기가 더 쉬워집니다.

프로그램 설정을 시도하기 전에 먼저 올바르게 설치되었는지 확인하세요.

* 모드 매니저를 사용할 경우, 아래 BodySlide 설치 및 실행 지침을 따라 주세요.
* 일반적으로 BodySlide 또는 바디 모드를 다운로드한 모드 페이지의 설명을 반드시 읽어 보세요.

### 관련 문서

* 명령줄 실행과 자동화 옵션은 [명령줄 인수](Command%E2%80%90line-arguments.md)를 참고하세요.
* Outfit Studio 자동화 스크립트는 [Automation Dialog](Automation-Dialog.md)를 참고하세요.
* 소스 빌드와 자동 테스트 설정은 [테스트 실행](Running-Tests.md)을 참고하세요.

***

#### 수동 설치

1. 파일을 다운로드한 뒤 7-Zip을 사용해 게임 설치 폴더의 "Data" 폴더 안에 압축을 풉니다.
2. 폴더 구조가 올바른지 확인하세요. Skyrim은 "_\<game folder\>/Data/CalienteTools/BodySlide_", FO4 및 기타 게임은 "_\<game folder\>/Data/Tools/BodySlide_" 구조여야 합니다.
3. 설치가 끝나면 위 폴더 안에서 실행 파일을 찾아 실행할 수 있습니다.

#### Vortex

1. 다른 모드와 같은 방식으로 아카이브 파일을 Vortex에 다운로드 및 설치한 뒤 활성화합니다.
2. "Mods" 섹션에서 "Deploy Mods" 툴바 버튼을 눌러 Vortex가 올바르게 배포했는지 확인합니다.
3. 대시보드에서 "Add Tool"로 이동합니다.
4. "Target" 필드에서 게임 설치 폴더의 실제 data 폴더에 있는 "BodySlide x64.exe" 파일을 선택합니다. Vortex mods 폴더가 **아닙니다**. Skyrim은 _"\<game folder\>/Data/CalienteTools/BodySlide"_, FO4 및 기타 게임은 _"\<game folder\>/Data/Tools/BodySlide"_ 경로입니다.
5. 바디 모드와 의상 같은 BodySlide 애드온도 Vortex에 함께 설치합니다.

[Vortex 설치 과정 GIF](https://staticdelivery.nexusmods.com/mods/1704/images/201/201-1537370120-1864925415.gif)

#### Mod Organizer

1. 다른 모드와 같은 방식으로 아카이브 파일을 MO에 다운로드 및 설치한 뒤 활성화합니다.
2. "Data" 탭에서 "BodySlide x64.exe" 파일의 바로가기를 추가하고, MO mods 폴더가 **아니라** 게임의 실제 data 폴더에서 실행되도록 설정합니다. Skyrim은 _"\<game folder\>/Data/CalienteTools/BodySlide"_, FO4 및 기타 게임은 _"\<game folder\>/Data/Tools/BodySlide"_ 경로입니다.
3. 바디 모드와 의상 같은 BodySlide 애드온도 MO에 함께 설치합니다.

#### 문제 해결

* 사용 중인 게임에 맞는 바디 모드를 설치했는지 확인하세요. 예를 들어 Skyrim SE/AE에는 CBBE LE가 아니라 CBBE SE를 다운로드해야 합니다.
* Vortex나 MO 같은 모드 매니저를 사용한다면, 먼저 다른 모드들이 게임 안에서 정상적으로 작동하는지 확인하세요.
* Vortex나 MO 같은 모드 매니저를 사용한다면, BodySlide 바로가기가 Vortex/MO 전용 mods 폴더가 아니라 실제 게임 폴더, 즉 Steam 폴더를 가리키도록 설정하세요.
* 모드 매니저와 관련해 추가 도움이 필요하다면 각 모드 매니저 커뮤니티에 문의하세요.

***

## 대상 게임

실행 파일을 처음 실행하면 다음 대화창이 표시됩니다.

[![Target Game](https://i.imgur.com/B2bocmem.png)](https://i.imgur.com/B2bocme.png)

BodySlide와 Outfit Studio에 사용할 게임의 "Data" 폴더를 선택한 뒤 계속 진행합니다.

레지스트리에서 발견된 게임은 경로가 자동으로 채워집니다. 하지만 한 번에 선택할 수 있는 대상 게임은 하나뿐입니다. 이 선택은 나중에 설정 대화창에서 변경할 수 있습니다.

## 설정

프로그램의 설정 대화창은 BodySlide 메인 창에서 열 수 있습니다.

[![Settings](https://i.imgur.com/AaTBoawm.png)](https://i.imgur.com/AaTBoaw.png)

### Game

**Target Game**  
BodySlide와 Outfit Studio를 사용할 대상 게임입니다. 이 옵션을 변경하면 게임 data 경로와 레퍼런스 스켈레톤도 함께 조정되므로, 두 설정이 올바른지 확인하세요.

**Game Data Path**  
현재 대상 게임의 "Data" 폴더를 가리켜야 하는 경로입니다. 프로그램이 리소스를 어디에서 불러올지, 프로젝트의 출력 파일을 어디에 생성할지 판단하는 데 사용됩니다.

**Advanced: Output Path**  
출력 파일을 생성할 경로를 선택적으로 덮어쓰는 설정입니다. 이 항목을 입력하면 리소스는 게임 data 경로에서 불러오고, BodySlide의 빌드 결과물은 출력 경로에 생성됩니다.

**Advanced: Project Path**  
BodySlide 프로젝트와 관련된 파일을 불러올 경로를 선택적으로 덮어쓰는 설정입니다. 비워 두면 실행 파일이 있는 디렉터리가 대신 사용됩니다.

### General

**Override Warning**  
배치 빌드에서 여러 프로젝트가 같은 출력 파일을 덮어쓰려고 할 때 표시되는 선택 대화창을 켜거나 끕니다.

**Left Mouse Pan**  
Outfit Studio에서 왼쪽 마우스 버튼으로 화면을 이동하는 기능을 켜거나 끕니다. 단, 왼쪽 마우스 버튼은 브러시 작업에도 사용된다는 점을 기억하세요.

**BSA Textures**  
미리보기 창의 텍스처 같은 리소스를 찾기 위해 data 폴더 안의 BSA/BA2 아카이브를 스캔할지 여부를 켜거나 끕니다.

**Language**  
해당 언어의 번역 파일이 존재하고 번역되어 있다면, 선택한 언어를 프로그램에 적용합니다.

### Data Files

필요에 따라 재질 또는 텍스처 파일 같은 리소스를 찾기 위해 스캔할 BSA/BA2 아카이브 목록입니다. 성능을 위해 이 목록은 가능한 한 최소한으로 유지하는 것이 좋습니다. 예를 들어 사운드 파일만 들어 있는 아카이브는 비활성화할 수 있습니다.

### Rendering

**Background Color**  
BodySlide와 Outfit Studio 렌더 창의 배경색입니다.

### Reference Skeleton

**File**  
Outfit Studio가 본 목록을 만들고 본 트랜스폼을 읽어올 때 사용하는 레퍼런스 스켈레톤 파일입니다.

**Root Node**  
루트 노드 이름은 게임마다 다를 수 있습니다. Outfit Studio가 본 목록을 어디서부터 읽기 시작해야 하는지 알 수 있도록 이 항목을 올바르게 설정해야 합니다.

## Config.xml

일부 옵션은 현재 Config.xml 파일 안에서만 확인할 수 있습니다.

**GroupAliases**  
그룹 별칭은 예전 그룹 이름으로 저장된 프리셋이 그룹 이름이 변경된 뒤에도 계속 적용될 수 있게 해 줍니다. 여러 그룹을 서로 연결해 하나의 그룹으로 합칠 수도 있습니다.

**SliderMinimum and SliderMaximum**  
BodySlide UI의 최소 및 최대 슬라이더 값을 설정합니다. 이 옵션을 사용하면 슬라이더를 더 쉽게 실험해 볼 수 있습니다. 0-100 범위를 벗어나면 클리핑이 생길 수 있으며, 지원되는 사용 방식이 아닙니다!
