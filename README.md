# ITConnect 바이브코딩 플러그인 마켓플레이스

아이티커넥트의 비개발자용 바이브코딩 교육 플러그인 배포 저장소입니다. 같은 교육 과정을 Claude Code와 Codex에서 사용할 수 있도록 플랫폼별 플러그인을 함께 제공합니다.

| 플랫폼 | 플러그인 | 실행 방식 |
|---|---|---|
| Claude Code | `plugins/vibe-pipeline` | `/vibe:01-prd` |
| Codex CLI·데스크톱 앱 | `plugins/vibe` | `$vibe:01-prd` |

두 플러그인은 PRD → 디자인 프롬프트 → FRD → TRD → 개발 계획 → STORY 개발 순서를 동일하게 따릅니다.

## 가장 쉬운 설치 방법 — 터미널 명령어 없이

### A. Antigravity의 Claude Code 확장프로그램에서 설치

Antigravity 안에 Claude Code 확장프로그램이 설치돼 있다면 PowerShell을 열지 않고 확장 화면에서 설치할 수 있습니다.

1. Antigravity에서 **Claude Code 패널**을 엽니다.
2. Claude Code 입력창에 `/plugins`를 입력해 **Manage plugins** 화면을 엽니다.
3. 상단의 **Marketplaces** 탭을 선택합니다.
4. 마켓플레이스 입력란에 `itconnect-ai/itconnect-vibe-plugins`를 붙여넣고 추가합니다.
5. **Plugins** 탭으로 돌아가 `vibe`를 검색합니다.
6. `vibe`의 **Install**을 누릅니다.
7. 설치 범위는 모든 프로젝트에서 사용할 수 있는 **Install for you**를 권장합니다.
8. 재시작 안내 배너가 나타나면 Claude Code를 재시작하고 새 대화를 엽니다.

설치 후 다음처럼 시작합니다.

```text
/vibe:01-prd 만들고 싶은 서비스 아이디어
```

Antigravity IDE는 [VS Code 코드베이스 기반 편집기](https://antigravity.google/docs/editor)이므로 설치된 Claude Code 확장이 최신 플러그인 관리 화면을 제공할 때 위 절차를 사용할 수 있습니다. `/plugins`가 그래픽 화면을 열지 않으면 확장프로그램을 업데이트한 뒤 다시 시도하고, 계속 지원되지 않으면 아래의 명령어 설치 방법을 사용합니다.

[Claude Code 확장프로그램의 플러그인 관리 공식 안내](https://code.claude.com/docs/en/vs-code#manage-plugins)

### B. ChatGPT 데스크톱 앱에서 Codex용 플러그인 설치

현재 `vibe`는 공개 Plugins Directory 등록본이 아니라 GitHub 저장소 마켓플레이스입니다. 따라서 GitHub 저장소를 로컬 프로젝트로 연 뒤 ChatGPT 데스크톱의 Plugins 화면에서 설치합니다.

1. [플러그인 GitHub 저장소](https://github.com/itconnect-ai/itconnect-vibe-plugins)에서 **Code → Open with GitHub Desktop**을 선택합니다.
2. GitHub Desktop에서 원하는 폴더를 선택해 저장소를 복제합니다.
3. ChatGPT 데스크톱 앱을 열고 **Codex**를 선택합니다.
4. 프로젝트 열기에서 복제한 `itconnect-vibe-plugins` 최상위 폴더를 선택합니다. `plugins/vibe` 하위 폴더가 아니라 저장소 전체를 열어야 합니다.
5. ChatGPT 데스크톱 앱을 한 번 재시작합니다.
6. **Plugins**를 열고 마켓플레이스 목록에서 **ITConnect Education**을 선택합니다.
7. **Vibe Pipeline**을 열어 `+` 버튼으로 설치합니다.
8. 새 Codex 작업을 엽니다.

설치 후 다음처럼 시작합니다.

```text
$vibe:01-prd 만들고 싶은 서비스 아이디어
```

**ITConnect Education**이 보이지 않으면 복제한 저장소의 최상위 폴더를 프로젝트로 열었는지 확인한 뒤 앱을 재시작합니다. ChatGPT 데스크톱은 저장소 루트의 `.agents/plugins/marketplace.json`을 읽어 로컬 마켓플레이스를 표시합니다.

[ChatGPT·Codex 플러그인 사용 공식 안내](https://learn.chatgpt.com/docs/plugins) · [저장소 마켓플레이스 공식 안내](https://developers.openai.com/plugins/build/plugins#build-your-own-curated-plugin-list)

## 명령어로 설치하기 — 대안

### Claude Code

```bash
claude plugin marketplace add itconnect-ai/itconnect-vibe-plugins
claude plugin install vibe@itconnect
```

Claude Code CLI 안에서는 다음 명령을 사용할 수 있습니다.

```text
/plugin marketplace add itconnect-ai/itconnect-vibe-plugins
/plugin install vibe@itconnect
```

수강생용 시작 템플릿의 `.claude/settings.json`에 다음 설정을 넣으면 설치를 제안할 수 있습니다.

```json
{
  "extraKnownMarketplaces": {
    "itconnect": {
      "source": {
        "source": "github",
        "repo": "itconnect-ai/itconnect-vibe-plugins"
      }
    }
  },
  "enabledPlugins": {
    "vibe@itconnect": true
  }
}
```

### Codex

Codex CLI 또는 Codex 데스크톱 앱의 터미널에서 실행합니다.

```bash
codex plugin marketplace add itconnect-ai/itconnect-vibe-plugins --ref main
codex plugin add vibe@itconnect
```

설치 후 새 Codex 작업을 열고 다음처럼 시작합니다.

```text
$vibe:01-prd 만들고 싶은 서비스 아이디어
```

Codex CLI에서 `/plugins`를 입력하면 설치·활성화 상태를 확인할 수 있습니다. Codex 플러그인은 현재 IDE 확장에서 지원되지 않으므로 Codex CLI 또는 데스크톱 앱을 사용해야 합니다.

## 사용 순서

| 순서 | Claude Code | Codex | 하는 일 | 산출물 |
|---|---|---|---|---|
| 1 | `/vibe:01-prd` | `$vibe:01-prd` | 아이디어 구체화와 PRD 작성 | `docs/prd.md` |
| 2 | `/vibe:02-design` | `$vibe:02-design` | 디자인 시안 생성용 프롬프트 작성 | `docs/design-prompt.md` |
| 3 | `/vibe:03-frd` | `$vibe:03-frd` | 시안 대조, 기능 분해와 정책 결정 | `docs/frd.md` |
| 4 | `/vibe:04-trd` | `$vibe:04-trd` | 기술 스택과 구조 결정 | `docs/trd.md` |
| 5 | `/vibe:05-plan` | `$vibe:05-plan` | EPIC/STORY 개발 계획 수립 | `docs/plan.md` |
| 반복 | `/vibe:build` | `$vibe:build` | 다음 STORY 한 개 구현과 확인 | 코드와 `docs/plan.md` |
| 수시 | `/vibe:status` | `$vibe:status` | 현재 진행 상황 확인 | 화면 안내 |

2단계에서 만든 프롬프트는 Claude Design 또는 Google Stitch에 붙여넣고, 완성된 시안 이미지는 `design/01-home.png` 형식으로 저장합니다.

## 운영자 가이드

### Claude Code 검증과 업데이트

```bash
claude plugin validate . --strict
```

`plugins/vibe-pipeline/.claude-plugin/plugin.json`의 버전을 올린 뒤 푸시합니다.

### Codex 검증과 업데이트

Codex용 스킬과 플러그인을 각각 검증한 뒤 `plugins/vibe/.codex-plugin/plugin.json`의 버전을 올립니다. 학생은 다음 명령으로 마켓플레이스를 새로 받고 플러그인을 다시 설치합니다.

```bash
codex plugin marketplace upgrade itconnect
codex plugin add vibe@itconnect
```

업데이트 후 새 Codex 작업을 열어야 변경된 스킬이 적용됩니다.

## 저장소 구조

```text
.claude-plugin/marketplace.json       # Claude Code 마켓플레이스
.agents/plugins/marketplace.json      # Codex 마켓플레이스
plugins/
├── vibe-pipeline/                     # Claude Code용 플러그인
│   ├── .claude-plugin/plugin.json
│   └── skills/
└── vibe/                              # Codex용 플러그인
    ├── .codex-plugin/plugin.json
    └── skills/
```
