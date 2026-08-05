# Vibe Pipeline for Codex

비개발자가 아이디어에서 시작해 PRD, 디자인 프롬프트, FRD, TRD, 개발 계획을 만들고 STORY 단위로 개발하는 Codex 교육 플러그인입니다.

## 실행 순서

| 순서 | 스킬 | 산출물 |
|---|---|---|
| 1 | `$vibe:01-prd` | `docs/prd.md` |
| 2 | `$vibe:02-design` | `docs/design-prompt.md` |
| 3 | `$vibe:03-frd` | `docs/frd.md` |
| 4 | `$vibe:04-trd` | `docs/trd.md` |
| 5 | `$vibe:05-plan` | `docs/plan.md` |
| 반복 | `$vibe:build` | 코드와 계획 체크 |
| 수시 | `$vibe:status` | 현재 진행 상황 |

각 스킬은 명시적으로 선택해야 실행됩니다. 첫 단계는 다음처럼 호출합니다.

```text
$vibe:01-prd 만들고 싶은 서비스 아이디어
```
