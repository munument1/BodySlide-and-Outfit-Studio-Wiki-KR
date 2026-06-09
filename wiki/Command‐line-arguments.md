## BodySlide 명령줄 인수

### 개요

```
BodySlide [--groupbuild <groups>] [--targetdir <path>] [--preset <name>] [--trimorphs] [--preview <files>]
```

### 옵션

| 단축 | 전체 | 유형 | 설명 |
|-------|------|------|-------------|
| `-gbuild` | `--groupbuild` | `string` | 실행 시 빌드할 그룹 이름들의 목록입니다 (쉼표 구분). 지정하면 BodySlide가 그룹 빌드를 수행한 뒤 종료합니다. |
| `-t` | `--targetdir` | `string` | 빌드 결과물이 저장될 디렉터리입니다. 기본값은 설정된 게임 데이터 경로입니다. 경로 구분자가 누락된 경우 자동으로 추가됩니다. |
| `-p` | `--preset` | `string` | 빌드에 사용할 프리셋입니다. 기본값은 마지막으로 사용한 프리셋입니다. |
| `-tri` | `--trimorphs` | 스위치 | 빌드 시 .tri 모프 출력을 활성화합니다. |
| `-preview` | `--preview` | `string` | 미리보기 모드에서 열 파일 경로(`.nif` 또는 `.osp`) 목록입니다 (쉼표, 세미콜론 또는 파이프로 구분). 지정하면 BodySlide가 메인 창을 표시하지 않고 즉시 미리보기 창을 엽니다. 자세한 내용은 [미리보기 모드](#미리보기-모드)를 참고하세요. |

### 사용 예시

**기본 프리셋으로 단일 그룹 빌드:**
```
BodySlide --groupbuild "MyGroup"
```

**커스텀 디렉터리에 .tri 모프를 포함하여 여러 그룹 빌드:**
```
BodySlide --groupbuild "CBBE,CBBE Vanilla Outfits" --targetdir "C:\Output" --preset "CBBE Curvy" --trimorphs
```

**NIF 파일 미리보기:**
```
BodySlide --preview "mesh1.nif,mesh2.nif"
```

**OSP 프로젝트 파일의 모든 슬라이더 세트 미리보기:**
```
BodySlide --preview "project.osp"
```

**OSP 파일에서 특정 슬라이더 세트 미리보기:**
```
BodySlide --preview "project.osp?SetName1?SetName2"
```

**OSP 프로젝트와 추가 NIF 파일을 함께 미리보기:**
```
BodySlide --preview "project.osp?MySet,extra.nif"
```

### 미리보기 모드

`--preview` 옵션은 `.nif`와 `.osp`(BodySlide 프로젝트) 파일을 모두 지원합니다. 동작 방식은 파일 확장자와 명시적인 슬라이더 세트 이름 제공 여부에 따라 달라집니다.

외부 파일 목록은 쉼표, 세미콜론 또는 파이프를 기준으로 나뉩니다. 단일 `.osp` 항목 내부에서는 `?`를 사용해 프로젝트 경로와 하나 이상의 명시적인 슬라이더 세트 이름을 구분합니다.

**NIF 파일**

단순 `.nif` 경로는 미리보기 창에 메시로 직접 로드됩니다.

**OSP 파일**

`.osp` 파일은 하나 이상의 슬라이더 세트를 포함하는 BodySlide 프로젝트 파일입니다. `?` 문자는 `.osp` 파일에서 로드할 슬라이더 세트를 지정하는 구분자로 사용됩니다.

```
path/to/file.osp?SetNameA?SetNameB
```

| 구문 | 동작 |
|--------|----------|
| `file.osp` | 파일 내의 모든 슬라이더 세트를 찾아 드롭다운 목록에 표시합니다. |
| `file.osp?Set1` | 지정된 이름의 슬라이더 세트만 로드합니다. |
| `file.osp?Set1?Set2` | 지정된 여러 세트를 함께 로드합니다 (멀티 프로젝트 모드). |

### 참고 사항

- `--groupbuild` 옵션은 지정된 그룹에 속한 모든 의상의 배치 빌드를 트리거하며, 작업이 완료되면 애플리케이션을 종료합니다.
- `--preview` 옵션은 일반 실행 모드와 함께 사용할 수 없습니다. 메인 BodySlide 창은 표시되지 않습니다.
- `--targetdir` 및 `--preset` 옵션은 `--groupbuild`와 함께 사용할 때만 의미가 있습니다.

## Outfit Studio 명령줄 인수

### 개요

```
OutfitStudio [--project <name>] [--single-instance <yes|no>] [--automation <script>] [<file> ...]
```

### 옵션

| 단축 | 전체 | 유형 | 설명 |
|-------|------|------|-------------|
| `-proj` | `--project` | `string` | 실행 시 불러올 프로젝트의 이름입니다. |
| `-single` | `--single-instance` | `string` | 단일 인스턴스 동작을 강제합니다. `yes`는 파일을 이미 실행 중인 인스턴스로 보내고, `no`는 항상 새 인스턴스를 엽니다. 생략하면 애플리케이션의 기본/설정된 동작을 따릅니다. |
| `-a` | `--automation` | `string` | 지정된 이름의 자동화 스크립트(`.xml` 확장자 제외)를 헤드리스 모드로 실행합니다. |
| | *(위치 인자)* | `string` | 열려는 하나 이상의 파일 경로입니다. 여러 파일을 지정할 수 있습니다. `--automation`이 사용된 경우, 이 인자들은 배치 모드 스크립트의 배치 입력값이 됩니다. |

### 사용 예시

**새 인스턴스에서 파일 열기:**
```
OutfitStudio --single-instance no model.nif
```

**이름으로 프로젝트 열기:**
```
OutfitStudio --project "MyProject"
```

**이미 실행 중인 인스턴스로 파일 보내기:**
```
OutfitStudio --single-instance yes mesh.nif
```

**여러 파일 열기:**
```
OutfitStudio file1.nif file2.nif file3.obj
```

**자동화 스크립트 실행:**
```
OutfitStudio --automation "ConvertFromBodyAtoB" file1.nif file2.nif
```

**디렉터리에 대해 폴더 스캔 자동화 실행:**
```
OutfitStudio --automation "ProcessFolder" "D:\Meshes"
```

### 참고 사항

- 위치 파일 인자는 선택 사항이며 여러 파일을 지원합니다.
- `--single-instance yes`를 사용했을 때 인스턴스가 이미 실행 중이라면, 파일들은 IPC(Windows의 경우 DDE, 기타 플랫폼의 경우 TCP)를 통해 해당 인스턴스로 전달됩니다.
- `--project` 옵션은 불러온 파일들 중 어떤 프로젝트를 선택할지 지정합니다.
- `--automation`이 사용되면 위치 인자들은 배치 입력값으로 취급됩니다: **Folder Scan**의 경우 파일 경로 또는 디렉터리, **Slider Sets**의 경우 슬라이더 세트 프로젝트 이름입니다.
- 배치 모드가 아닌 자동화 스크립트는 위치 인자를 무시합니다.
