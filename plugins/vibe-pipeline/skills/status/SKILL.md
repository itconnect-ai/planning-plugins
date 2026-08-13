---
name: status
description: 파이프라인 진행 현황을 요약하고 다음 명령을 알려준다
disable-model-invocation: true
---

## 지금 상태

- docs 파일: !`ls -1 docs/ 2>/dev/null || echo "(docs/ 없음)"`
- 문서 상태 줄: !`grep -H "^상태:" docs/*.md 2>/dev/null || echo "(상태 줄 없음)"`
- 시안 파일: !`ls -1 design/ 2>/dev/null || echo "(design/ 없음)"`
- 개발 계획 체크 현황: !`grep "^- \[" docs/plan.md 2>/dev/null || echo "(plan 없음)"`

## 할 일

위에 주입된 정보만으로 판단해 5줄 이내로 답한다. 파일을 추가로 열지 않는다.

1. 전체 흐름에서 현재 위치: `1 PRD → 2 시안 → 3 FRD → 4 TRD → 5 계획 → 개발` 중 어디까지 완료됐는지 (prd.md, design/ 이미지, frd.md, trd.md, plan.md 존재 여부로 판단. setup.md는 1단계가 만드는 시작 설정 파일이므로 단계 판단에서 제외. "상태: 작성 중"인 문서는 완료로 치지 않고 해당 단계 명령 재실행을 안내)
2. 개발 단계라면 STORY 진행률: 완료 `[x]` 개수 / 전체 개수, 그리고 다음 미완료 STORY 이름
3. 지금 입력해야 할 명령 딱 1개 (예: `/vibe:03-frd`)

길게 설명하지 않는다. 격려 문구를 붙이지 않는다.
