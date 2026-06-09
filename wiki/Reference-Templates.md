## 레퍼런스 템플릿이란 무엇인가요?

레퍼런스 템플릿은 Outfit Studio에서 알려진 슬라이더 세트를 레퍼런스로 불러오기 위한 재사용 가능한 바로가기입니다. 템플릿 자체는 프로젝트 파일이 아닙니다. 템플릿은 오직 어떤 슬라이더 세트 파일, 어떤 세트 이름, 그리고 선택적으로 어떤 쉐이프를 불러올지를 Outfit Studio에 알려주는 역할만 합니다.

템플릿은 다음에서 사용됩니다:

* Outfit Studio의 **Load Reference** 대화 상자
* **Convert Body / Reference**와 같은 변환 워크플로우
* 자동화(Automation) 대화 상자의 **Load Reference** 단계 (템플릿을 선택하면 소스 파일, 세트, 쉐이프 및 `Load all shapes` 옵션이 자동으로 채워짐)

## 템플릿을 불러오는 위치

Outfit Studio는 BodySlide 폴더 내의 다음 두 위치에서 레퍼런스 템플릿을 불러옵니다:

* `RefTemplates.xml`
* `RefTemplates` 폴더 내의 모든 `.xml` 파일

이를 통해 모드 제작자는 사용자가 모든 내용을 하나의 파일로 병합할 필요 없이 추가 템플릿 팩을 제공할 수 있습니다.

## XML 형식

다음과 같은 구조를 사용합니다:

```xml
<RefTemplates>
    <Template sourcefile="SliderSets/CBBE.osp" set="CBBE Body" shape="CBBE">CBBE Body</Template>
    <Template sourcefile="ConversionSets/VanillaToCBBE.osp" set="Vanilla To CBBE" loadAll="true">Vanilla To CBBE</Template>
</RefTemplates>
```

각 `<Template>` 요소는 다음 값들을 지원합니다:

* **텍스트 내용(Text content)**은 템플릿 목록에 표시되는 이름입니다.
* **sourcefile**은 슬라이더 세트가 포함된 `.osp` 파일을 가리킵니다. 상대 경로는 BodySlide 폴더를 기준으로 해석됩니다. 절대 경로도 작동하지만, 배포용 템플릿 팩에는 보통 상대 경로가 더 좋습니다.
* **set**은 해당 `.osp` 파일 내의 슬라이더 세트 이름입니다.
* **shape**은 단일 레퍼런스 쉐이프를 불러올 때 레퍼런스가 될 쉐이프의 이름입니다.
* **loadAll**은 동작 방식을 "하나의 레퍼런스 쉐이프 불러오기"에서 "이 슬라이더 세트의 모든 쉐이프 추가하기"로 변경합니다. `loadAll="true"`인 경우 `shape` 속성은 무시됩니다.

## 좋은 템플릿 정의하기

### 단일 레퍼런스 템플릿

알려진 베이스/레퍼런스 쉐이프를 사용하고 싶을 때 사용합니다.

```xml
<Template sourcefile="SliderSets/CBBE.osp" set="CBBE Body" shape="CBBE">CBBE Body</Template>
```

`shape`가 생략되면 Outfit Studio는 참조된 NIF에서 발견되는 첫 번째 쉐이프를 대신 사용합니다. 작동은 하겠지만, 의도한 쉐이프 이름을 명시적으로 지정하는 것이 더 안전합니다.

### 전체 로드(Load-all) 템플릿

하나의 베이스 쉐이프를 선택하는 대신 선택한 슬라이더 세트의 모든 쉐이프를 임포트해야 할 때 사용합니다.

```xml
<Template sourcefile="ConversionSets/VanillaToCBBE.osp" set="Vanilla To CBBE" loadAll="true">Vanilla To CBBE</Template>
```

이는 변환 세트나 기타 다중 쉐이프 레퍼런스에 유용합니다.

## 패키징 및 구성

* 템플릿은 루트의 `RefTemplates.xml` 파일에 둘 수도 있고, `RefTemplates` 폴더 내의 여러 XML 파일로 나눌 수도 있습니다.
* 모드 전용 템플릿을 별도의 파일로 유지하면 업데이트가 쉬워지고 병합 충돌(Merge conflict)을 피할 수 있습니다.
* 템플릿 이름은 단순히 표시용 라벨이므로, 선택기에서 중복되어 혼란을 주지 않도록 고유한 이름을 사용하세요.

## BodySlide 사용자에게 템플릿 숨기기

어떤 프로젝트를 Outfit Studio에서 레퍼런스 템플릿으로만 사용하고 일반적인 BodySlide 프로젝트 목록에는 표시하고 싶지 않다면, 참조된 `.osp` 파일을 일반 사용자들이 직접 탐색하는 `SliderSets` 목록 외부에 두세요. 예를 들어, 변환 전용 프로젝트들은 `ConversionSets`와 같은 별도 폴더에 두면서도 템플릿 XML에서 참조할 수 있습니다.

## 관련 페이지

* [[변환 레퍼런스와 그 사용법|Conversion-references-and-using-them]]
* [[자동화 대화 상자|Automation-Dialog]]
