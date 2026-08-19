# ITConnect 바이브코딩 플러그인 마켓플레이스

아이티커넥트의 비개발자용 바이브코딩 교육 플러그인 배포 저장소입니다. 같은 교육 과정을 Claude Code와 Codex에서 사용할 수 있도록 플랫폼별 플러그인을 함께 제공합니다.

| 플랫폼 | 플러그인 | 실행 방식 |
|---|---|---|
| Claude Code | `plugins/vibe-pipeline` | `/vibe:01-prd` |
| Codex CLI·데스크톱 앱 | `plugins/vibe` | `$vibe:01-prd` |

두 플러그인은 PRD → 디자인 기준과 시안 → FRD → TRD → 개발 계획 → STORY 개발 순서를 동일하게 따릅니다.

## 가장 쉬운 설치 방법 — 터미널 명령어 없이

### A. Antigravity의 Claude Code 확장프로그램에서 설치

Antigravity 안에 Claude Code 확장프로그램이 설치돼 있다면 PowerShell을 열지 않고 확장 화면에서 설치할 수 있습니다.

1. Antigravity에서 **Claude Code 패널**을 엽니다.
2. Claude Code 입력창에 `/plugins`를 입력해 **Manage plugins** 화면을 엽니다.
3. 상단의 **Marketplaces** 탭을 선택합니다.
4. 마켓플레이스 입력란에 `itconnect-ai/planning-plugins`를 붙여넣고 추가합니다.
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

1. [플러그인 GitHub 저장소](https://github.com/itconnect-ai/planning-plugins)에서 **Code → Open with GitHub Desktop**을 선택합니다.
2. GitHub Desktop에서 원하는 폴더를 선택해 저장소를 복제합니다.
3. ChatGPT 데스크톱 앱을 열고 **Codex**를 선택합니다.
4. 프로젝트 열기에서 복제한 `planning-plugins` 최상위 폴더를 선택합니다. `plugins/vibe` 하위 폴더가 아니라 저장소 전체를 열어야 합니다.
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
claude plugin marketplace add itconnect-ai/planning-plugins
claude plugin install vibe@itconnect
```

Claude Code CLI 안에서는 다음 명령을 사용할 수 있습니다.

```text
/plugin marketplace add itconnect-ai/planning-plugins
/plugin install vibe@itconnect
```

> **설치 후 Claude Code를 완전히 껐다 다시 켜야 합니다.** 재시작 전에는 `/vibe:...` 명령이 목록에 나타나지 않습니다. 설치를 AI에게 대신 시킨 경우에도 재시작은 직접 해야 합니다. 재시작 후 `/vibe:help`를 입력하면 명령 목록과 진행 순서를 볼 수 있습니다.

수강생용 시작 템플릿의 `.claude/settings.json`에 다음 설정을 넣으면 설치를 제안할 수 있습니다.

```json
{
  "extraKnownMarketplaces": {
    "itconnect": {
      "source": {
        "source": "github",
        "repo": "itconnect-ai/planning-plugins"
      }
    }
  },
  "enabledPlugins": {
    "vibe@itconnect": true
  }
}
```

### Codex

일반 사용자는 이 저장소를 `git clone`하거나 `git pull`할 필요가 없고, 로컬 폴더 경로도 입력하지 않습니다. PowerShell 또는 터미널에서 아래 명령을 최초 한 번만 실행합니다.

```bash
codex plugin marketplace add itconnect-ai/planning-plugins --ref main
codex plugin add vibe@itconnect
```

설치 후 Codex를 완전히 종료하고 새 작업을 연 다음, 도움말부터 확인합니다.

```text
$vibe:help
```

바로 기획을 시작하려면 다음처럼 입력합니다.

```text
$vibe:01-prd 만들고 싶은 서비스 아이디어
```

Codex CLI에서 `/plugins`를 입력하면 설치·활성화 상태를 확인할 수 있습니다. Codex 플러그인은 현재 IDE 확장에서 지원되지 않으므로 Codex CLI 또는 데스크톱 앱을 사용해야 합니다.

## 업데이트와 새 프로젝트

### 새 버전 받기

플러그인이 개선되면 아래 순서로 받습니다. Claude Code는 `install`이 아니라 `update`를 사용하고, Codex는 마켓플레이스를 갱신한 뒤 `plugin add`를 다시 실행합니다.

Claude Code (CLI 안에서 `/plugin`으로도 가능합니다):

```bash
claude plugin marketplace update itconnect
claude plugin update vibe@itconnect
```

Codex:

```bash
codex plugin marketplace upgrade itconnect
codex plugin add vibe@itconnect
```

업데이트 후에는 **Claude Code를 재시작**하거나 **새 Codex 작업을 열어야** 적용됩니다. 일반 사용자는 저장소를 직접 `git clone`하거나 `git pull`할 필요가 없습니다 — 위 명령이 대신 처리합니다.

### 기존 프로젝트에 미치는 영향

- 플러그인은 Claude Code 또는 Codex의 사용자 전용 캐시에 설치되고, 학습자의 프로젝트 폴더에는 **스킬 파일이 하나도 들어가지 않습니다**. 프로젝트에는 `docs/`와 실제 코드만 생깁니다.
- 그래서 업데이트해도 이미 작성한 `docs/` 문서는 그대로 유지됩니다.
- 이전 버전에서 만든 문서(문서 첫머리에 `상태:` 줄이 없는 문서)는 완료된 문서로 간주하고 이어서 진행합니다.
- 구버전은 삭제되지 않고 버전별 폴더로 남아 있어 문제가 생기면 되돌릴 수 있습니다.

### 새 프로젝트 시작

재설치가 필요 없습니다. 빈 폴더에서 Claude Code는 `claude`를 실행한 뒤 `/vibe:help`, Codex는 `codex`를 실행한 뒤 `$vibe:help`를 입력합니다. 한 번 설치하면 같은 실행 환경의 모든 프로젝트에서 사용할 수 있습니다.

### 명령이 보이지 않을 때

`/vibe`를 입력했는데 명령이 하나도 없거나 일부만 보이면 아래 순서로 확인합니다.

1. **Claude Code를 껐다 켰는지 확인합니다.** 가장 흔한 원인입니다. 설치나 업데이트 직후에는 재시작 전까지 명령이 나타나지 않습니다.
2. **설치 상태를 확인합니다.** Claude Code 안에서 `/plugin`을 입력하거나, 터미널에서 `claude plugin list`를 실행하면 아래 항목이 보여야 합니다.

   ```text
   > vibe@itconnect
     Status: enabled
   ```

   목록에 없으면 설치가 안 된 것이므로 위 설치 명령을 다시 실행합니다. 상태가 `disabled`이면 `/plugin`에서 활성화합니다.
3. **자동완성 목록이 이상해도 명령 전체를 입력하면 실행됩니다.** `/vibe:03-frd`처럼 끝까지 입력해 보세요.
4. 그래도 안 되면 Claude Code에게 **"vibe 플러그인이 설치돼 있는지 확인해줘"**라고 요청하세요. 설치 여부와 버전을 확인해 알려줍니다.

Codex에서는 `/plugins`로 설치·활성화 상태를 확인하고, 스킬이 안 보이면 Codex를 종료한 뒤 새 작업을 엽니다.

## 사용 순서

| 순서 | Claude Code | Codex | 하는 일 | 산출물 |
|---|---|---|---|---|
| 1 | `/vibe:01-prd` | `$vibe:01-prd` | 아이디어 구체화와 PRD 작성 (첫 실행 시 대화 방식 설정 포함) | `docs/prd.md`, `docs/setup.md` |
| 2 | `/vibe:02-design` | `$vibe:02-design` | 디자인 기준 작성과 가능한 경우 시안 제작·검토 | `docs/design-prompt.md`, 화면 시안(선택) |
| 3 | `/vibe:03-frd` | `$vibe:03-frd` | 시안 대조, 기능 분해와 정책 결정 | `docs/frd.md` |
| 4 | `/vibe:04-trd` | `$vibe:04-trd` | 기술 스택과 구조 결정 | `docs/trd.md` |
| 5 | `/vibe:05-plan` | `$vibe:05-plan` | EPIC/STORY 개발 계획 수립 | `docs/plan.md` |
| 반복 | `/vibe:build` | `$vibe:build` | 다음 STORY 한 개 구현과 확인 | 코드와 `docs/plan.md` |
| 수시 | `/vibe:status` | `$vibe:status` | 현재 진행 상황 확인 | 화면 안내 |
| 도움말 | `/vibe:help` | `$vibe:help` | 명령 목록과 진행 순서 안내 | 화면 안내 |

2단계는 사용 가능한 도구가 있으면 AI가 화면 시안을 직접 만들거나 기존 HTML·이미지를 확인합니다. 도구가 없으면 `docs/design-prompt.md`를 Claude Design 또는 Google Stitch에서 사용하도록 안내합니다. 새로운 화면·기능·정책은 사용자 승인 없이 추가하지 않으며, 시안 이미지는 권장이지만 선택 산출물입니다 — 이미지가 없어도 3단계 진행이 가능합니다.

1단계 첫 실행 시 AI와의 대화 방식을 고릅니다 — 간단 모드는 제품의 모습을 정하는 핵심 결정만 묻고 나머지는 추천으로 채우며, 꼼꼼 모드는 결정을 하나씩 배우며 진행합니다. 어느 모드든 만들어지는 범위와 결과물은 같습니다. 완료 기준은 로컬 실행(localhost)이며, 배포는 계획의 마지막 "배포(선택)" EPIC으로 분리되어 강의에서 강사와 함께 진행할 수 있습니다.

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

### Codex 로컬 작업본 테스트 (운영자·개발자 전용)

GitHub에 푸시하기 전 로컬 변경을 시험할 때만 저장소 폴더를 마켓플레이스로 등록합니다. 저장소 루트에서 최초 한 번 실행합니다.

```bash
codex plugin marketplace add .
codex plugin add vibe@itconnect
```

이후 로컬 수정이나 `git pull` 뒤에는 폴더 경로를 다시 등록하지 않습니다. 플러그인 버전을 올린 뒤 아래 명령만 다시 실행하고 새 Codex 작업을 엽니다.

```bash
codex plugin add vibe@itconnect
```

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
