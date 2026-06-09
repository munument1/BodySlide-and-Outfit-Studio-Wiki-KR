BodySlide와 Outfit Studio 사용자 인터페이스의 대부분은 다른 언어로 번역할 수 있습니다. 이는 [wxWidgets](https://www.wxwidgets.org/) GUI 라이브러리에 내장된 기능을 통해 이루어집니다.

## 번역 만들기
**번역을 생성하거나 편집**하려면 무료 프로그램인 **[Poedit](https://poedit.net/)**을 사용하는 것이 좋습니다. 일반 텍스트 에디터로 수정하고 Poedit으로 컴파일할 수도 있지만, 권장되는 방법은 아닙니다.

[![Poedit](http://i.imgur.com/hz8LYKHt.png)](http://i.imgur.com/hz8LYKH.png)

편집하려는 언어 폴더 내에 있는 기존 **BodySlide.po** 파일을 찾으세요.  
예시:
* _BodySlide/lang/{언어 코드}/BodySlide.po_
* _[BodySlide/lang/de/BodySlide.po](../blob/dev/lang/de/BodySlide.po)_

.po 파일이 없고 새로운 번역을 만들고 싶다면, 대신 [lang/BodySlide.pot](../blob/dev/lang/BodySlide.pot) 템플릿 파일을 여세요.

템플릿이나 기존 번역 파일을 열었다면 편집을 시작할 수 있습니다. .pot 템플릿에 추가된 새로운 항목들로 .po 번역 파일을 업데이트하려면, Poedit에서 **Catalogue -> Update from POT file**을 선택하세요.

![Update from template](http://i.imgur.com/C3c8o1L.png)

모든 사용자가 혜택을 누릴 수 있도록 **[풀 리퀘스트(Pull request)](../pulls)**를 보낼 때 **.po**(소스 텍스트)와 **.mo**(컴파일된 텍스트) 파일을 모두 포함해 주세요!

## 번역 사용하기
실제로 사용되는 언어를 변경하려면 설정 대화 상자를 열어 언어 선택 옵션을 사용하세요 ([[설치 및 설정|Installation-and-Settings]] 참고).
