## 쉐이프 속성이란 무엇인가요?

Outfit Studio에서 **Shape -> Properties**를 열거나 쉐이프 목록에서 쉐이프를 더블 클릭하면, 셰이더 설정, 지오메트리 플래그, 엑스트라 데이터, 좌표 트랜스폼과 같은 메시 전용 메타데이터를 편집할 수 있습니다.

여러 개의 쉐이프를 선택한 상태에서 이 대화 상자를 열 수도 있습니다. 이 경우 Outfit Studio는 배치 편집(Batch-edit) 워크플로우로 전환됩니다:

* 대화 상자 제목에 선택된 쉐이프의 개수가 표시됩니다.
* **Geometry** 탭이 기본 탭이 됩니다.
* **Extra Data** 및 **Coordinates**와 같이 단일 쉐이프 전용인 탭은 비활성화됩니다.
* 선택된 모든 쉐이프에 안전하게 영향을 줄 수 있는 배치 작업들은 실행 전에 확인을 요청합니다.

현재 대화 상자에는 **Shader**, **Geometry**, **Extra Data**, **Coordinates**의 네 가지 탭이 있습니다.

[![Shader](http://i.imgur.com/R4ao6aKb.png)](http://i.imgur.com/R4ao6aK.png)
[![Geometry](http://i.imgur.com/50BYgYZb.png)](http://i.imgur.com/50BYgYZ.png)
[![Extra Data](http://i.imgur.com/SGoo36jb.png)](http://i.imgur.com/SGoo36j.png)
[![Coordinates](http://i.imgur.com/ApCWZwqb.png)](http://i.imgur.com/ApCWZwq.png)

## Shader (셰이더)

**Shader** 탭은 현재 쉐이프에 부착된 재질(Material)/셰이더 블록을 제어합니다.

### 기본 필드

* **Name / Material**은 구형 게임의 경우 셰이더 이름을 저장합니다. 폴아웃 4의 경우 할당된 `.bgsm` 또는 `.bgem` 재질 경로로 취급됩니다. 스타필드(Starfield)의 경우 할당된 `.mat` 재질 경로로 취급됩니다.
* 대상 게임이 외부 재질 파일을 지원하는 경우, 필드 옆의 **...** 버튼을 눌러 재질 선택기를 열 수 있습니다.
* **Type**은 지원되는 라이팅(Lighting) 셰이더의 유형을 변경합니다. 사용 가능한 목록은 셰이더 클래스와 게임에 따라 다릅니다.
* **Shading**은 폴아웃 3 / 뉴 베가스의 후처리 라이팅 셰이더에서 표시되며, 하드(Hard) 셰이딩과 스무드(Smooth) 셰이딩 사이를 전환할 수 있게 해 줍니다.
* **Specular Color**, **Specular Strength**, **Specular Power**, **Emissive Color**, **Emissive Multiple**, **Alpha**는 현재 대화 상자에서 지원하는 공통 라이팅/재질 수치들입니다.
* **Vertex Colors**는 셰이더에서 정점 컬러(Vertex-color) 사용 여부를 전환합니다. 정점 알파(Vertex alpha)를 활성화하면 정점 컬러도 자동으로 활성화됩니다.
* **Double Sided**는 양면 렌더링 여부를 전환합니다. 폴아웃 3 / 뉴 베가스는 일반적인 셰이더 플래그 대신 스텐실(Stencil) 속성을 통해 이를 저장하므로 동작 방식이 게임마다 다릅니다.

### 버튼

* **Add**는 아직 셰이더/재질 설정이 없는 쉐이프를 위해 기본 설정을 생성합니다.
* **Remove**는 선택된 쉐이프에서 셰이더 블록을 제거합니다.
* **Textures...**는 현재 셰이더의 텍스처 세트 에디터를 엽니다.
* **Copy from shape...**은 동일한 프로젝트 내의 다른 쉐이프로부터 셰이더 및 텍스처 할당 정보를 복제해옵니다.

### 셰이더 플래그 (Shader flags)

**Shader Flags** 접이식 섹션은 다음 게임별 전체 플래그 목록을 보여줍니다:

* 스카이림 계열 라이팅 셰이더
* 폴아웃 4 계열 라이팅 셰이더
* 폴아웃 3 / 뉴 베가스 셰이더 속성

대화 상자는 **Vertex Colors**, **Vertex Alpha**, **Double Sided**와 같은 공통 체크박스들을 대상 게임의 관련 플래그 비트와 동기화된 상태로 유지합니다.

### 고급 셰이더 속성 (Advanced shader properties)

**Advanced** 접이식 섹션은 더 이상 단순한 플레이스홀더가 아닙니다. 이제 Outfit Studio가 현재 셰이더 유형에 대해 직접 편집할 수 있는 고급 속성들을 노출합니다.

공통 필드에는 다음이 포함됩니다:

* **UV Offset** 및 **UV Scale**
* **Texture Clamp Mode**
* **Refraction Strength**
* **Environment Map Scale**

추가 필드들은 현재 셰이더 유형에 해당할 때만 나타납니다. 예시:

* **Skin Tint Color**
* **Hair Tint Color**
* **Parallax Max Passes** 및 **Parallax Scale**
* 다중 레이어 패럴랙스(Multilayer parallax)를 위한 **Inner Layer Thickness**, **Parallax Refraction Scale**, **Inner Layer Tex Scale**, **Parallax Envmap Strength**
* 눈(Snow) 셰이더를 위한 **Sparkle Parameters**
* 눈(Eye) 셰이더를 위한 **Eye Cubemap Scale** 및 좌우 반사 중심점

폴아웃 4 형식의 라이팅 셰이더는 다음과 같은 최신 재질 필드들도 노출합니다:

* **Wet Material**
* **Subsurface Rolloff**
* **Rimlight Power** 및 **Backlight Power**
* **Grayscale To Palette**
* **Fresnel Power**
* **Wetness Spec Scale**, **Wetness Spec Power**, **Wetness Min Var**, **Wetness Fresnel Power**, **Wetness Metalness**
* 파일 형식에 존재하는 경우 **Wetness Env Map Scale**

스타필드의 경우 이러한 컨트롤들이 스타필드 재질과 깔끔하게 매칭되지 않기 때문에 구형 셰이더 유형, 스펙큘러, 셰이더 플래그 및 고급 패널을 숨깁니다.

### 투명도 (Transparency)

**Transparency** 접이식 섹션은 쉐이프의 알파(Alpha) 속성을 관리합니다.

지원되는 컨트롤:

* **Threshold**
* **Vertex Alpha**
* **Alpha Test**
* **Alpha Blend**
* **Src Blend** 및 **Dest Blend**
* **Test Function**
* **No Sorter**
* 알파 속성 자체를 생성하거나 삭제하는 **Add** / **Remove**

선택된 쉐이프에 이미 알파 속성이 있는 경우, 대화 상자가 열릴 때 투명도 패널이 자동으로 확장됩니다.

## Geometry (지오메트리)

**Geometry** 탭은 여러 쉐이프를 다중 선택했을 때 배치 편집이 안전한 메시 형식 플래그들을 노출합니다. 여러 쉐이프가 선택된 경우, 체크박스는 세 가지 상태(Three-state)를 사용하여 현재 선택된 항목들이 일치하는지 여부를 보여줍니다.

* **Full Precision**은 선택된 메시 형식이 해당 플래그 변경을 지원하는 경우 전체 정밀도(Full-precision) 정점 저장을 전환합니다.
* **Sub Index**는 `BSTriShape`와 `BSSubIndexTriShape` 간을 변환합니다. 이를 활성화하면 Outfit Studio는 새로운 서브 인덱스 쉐이프를 위한 기본 세그먼트 레이아웃을 생성합니다.
* **Skinned**는 스키닝(Skinning) 데이터를 추가하거나 제거합니다. 이 옵션을 끄면 현재의 스키닝 설정이 제거되며, 다시 켜면 기본 스키닝 데이터가 재생성됩니다.
* **Dynamic**은 해당 구분을 지원하는 형식에서 `BSTriShape`와 `BSDynamicTriShape` 간을 변환합니다.

가용 여부는 게임 형식과 선택된 쉐이프 유형 모두에 따라 달라집니다. 체크박스가 비활성화되어 있다면 현재 메시는 해당 방식으로 변환할 수 없음을 의미합니다.

## Extra Data (엑스트라 데이터)

**Extra Data** 탭은 쉐이프에 부착된 `NiExtraData` 블록들을 편집합니다. 이 탭은 단일 쉐이프 편집 시에만 사용할 수 있습니다.

Outfit Studio는 현재 다음 모든 유형을 대화 상자에서 직접 생성하고 편집하는 것을 지원합니다:

* `NiStringExtraData`
* `NiIntegerExtraData`
* `NiFloatExtraData`
* `NiBooleanExtraData`
* `NiVectorExtraData`
* `NiColorExtraData`
* `NiIntegersExtraData`
* `NiStringsExtraData`
* `NiFloatsExtraData`
* `BSDistantObjectLargeRefExtraData`

각 항목에는 다음이 포함됩니다:

* **Remove** 버튼
* **유형(Type)** 선택기
* **이름(Name)** 필드
* 해당 데이터 유형에 적합한 값 에디터

단순한 문자열, 정수, 부동 소수점, 불리언 값은 인라인으로 편집할 수 있습니다. 벡터, 컬러 및 리스트 기반 엑스트라 데이터는 전용 에디터 대화 상자를 사용합니다:

* 벡터 및 컬러 항목은 각 컴포넌트별 필드가 있는 **Edit...** 대화 상자를 엽니다.
* 컬러 항목에는 컬러 피커 미리보기도 포함됩니다.
* 정수, 문자열, 부동 소수점 리스트는 **Add Row** 및 **Remove Row** 컨트롤이 있는 그리드 에디터를 엽니다.

알 수 없는 엑스트라 데이터 블록 유형은 이 대화 상자를 통해 노출되지 않습니다.

## Coordinates (좌표)

**Coordinates** 탭은 쉐이프의 로컬 공간에서 전역 공간으로의 트랜스폼을 편집합니다. 이는 메시 데이터와 쉐이프의 월드 배치 사이의 저장된 크기(Scale), 이동(Translation), 회전(Rotation) 차이값입니다.

다음을 편집할 수 있습니다:

* **Scale** (크기)
* **X / Y / Z** 이동
* **X / Y / Z** 회전

이 값들 중 하나라도 변경하면 Outfit Studio는 **Recalculate geometry's coordinates so it doesn't move** (쉐이프가 움직이지 않도록 지오메트리 좌표 다시 계산) 옵션을 활성화합니다. 이 박스를 체크된 상태로 두면, 저장된 트랜스폼이 변경되는 동안 시각적으로는 쉐이프가 동일한 위치에 머물도록 메시 정점들이 변환됩니다.

이 탭은 단일 쉐이프가 선택되었을 때만 활성화됩니다.

## 참고 사항

* 이 대화 상자는 이제 몇 가지 상위 레벨 셰이더 수치에만 국한되지 않습니다. 현재의 고급 셰이더 및 엑스트라 데이터 에디터는 이전에 NifSkope로 전환해야 했던 많은 공통 작업들을 수행하기에 충분히 유용합니다.
* 폴아웃 3 / 뉴 베가스는 여전히 특히 정점 알파 및 양면 렌더링 주변에서 몇 가지 엔진 전용 특이 사항이 있습니다.
* 레퍼런스 로딩, 텍스처 할당 및 재질 파일 동작은 여전히 대상 게임의 파일 형식에 따라 달라지므로, 흔치 않은 셰이더 조합을 변경하는 경우 항상 게임 내에서나 NifSkope에서 결과를 테스트하세요.
