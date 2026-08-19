# Vibe Pipeline for Codex

비개발자가 아이디어에서 시작해 PRD, 디자인 기준과 시안, FRD, TRD, 개발 계획을 만들고 STORY 단위로 개발하는 Codex 교육 플러그인입니다.

## 최초 설치

일반 사용자는 저장소를 직접 내려받거나 로컬 폴더 경로를 입력하지 않습니다. PowerShell 또는 터미널에서 아래 명령을 최초 한 번 실행합니다.

```bash
codex plugin marketplace add itconnect-ai/planning-plugins --ref main
codex plugin add vibe@itconnect
```

설치 후 새 Codex 작업을 열고 `$vibe:help`를 입력합니다. 새 프로젝트를 만들 때는 재설치할 필요가 없습니다.

## 업데이트

```bash
codex plugin marketplace upgrade itconnect
codex plugin add vibe@itconnect
```

업데이트 후에는 새 Codex 작업을 열어야 변경된 스킬이 적용됩니다.

## 실행 순서

| 순서 | 스킬 | 산출물 |
|---|---|---|
| 1 | `$vibe:01-prd` | `docs/prd.md`, `docs/setup.md` (첫 실행 시 대화 방식 설정) |
| 2 | `$vibe:02-design` | `docs/design-prompt.md`, 화면 시안(선택) |
| 3 | `$vibe:03-frd` | `docs/frd.md` |
| 4 | `$vibe:04-trd` | `docs/trd.md` |
| 5 | `$vibe:05-plan` | `docs/plan.md` |
| 반복 | `$vibe:build` | 코드와 계획 체크 |
| 수시 | `$vibe:status` | 현재 진행 상황 |
| 도움말 | `$vibe:help` | 명령 목록과 진행 순서 안내 |

각 스킬은 명시적으로 선택해야 실행됩니다. 첫 시작은 다음처럼 호출합니다.

```text
$vibe:01-prd 만들고 싶은 서비스 아이디어
```

1단계 첫 실행 시 AI와의 대화 방식을 고릅니다. 꼼꼼 모드는 라운드 수를 고정하지 않고 AI가 누락·모호·충돌 항목을 찾아 필요한 만큼 보완하며, 간단 모드는 기본 2라운드로 핵심 결정만 묻고 나머지는 추천·추정으로 채워 일괄 확인합니다. 어느 모드든 산출물과 기능 범위는 같습니다. 완료 기준은 로컬 실행이며, 배포는 계획의 마지막 "배포(선택)" EPIC으로 분리됩니다.

2단계는 사용 가능한 도구가 있으면 AI가 화면 시안을 직접 만들거나 기존 HTML·이미지를 확인합니다. 도구가 없으면 `docs/design-prompt.md`를 Claude Design 또는 Google Stitch에서 사용하도록 안내합니다. 새로운 화면·기능·정책은 사용자 승인 없이 추가하지 않으며, 시안 이미지는 선택 산출물입니다.
