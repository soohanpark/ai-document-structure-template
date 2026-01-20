# Planning Docs

> **Template instructions | 템플릿 안내**
>
> This folder stores feature planning and product specification documents.
> 이 폴더는 기능 기획서와 제품 스펙 문서를 모아 관리합니다.
>
> **Source of truth**: [CLAUDE.md](../../CLAUDE.md)

---

## Purpose | 목적

- Keep feature intent, scope, and trade-offs documented in one place
- Provide AI agents with clear, structured context when implementing features
- Make it easy to review decisions before work starts

---

## When to Add a Doc | 언제 문서를 추가하나요?

- New feature planning (기능 추가 기획)
- Significant behavior change (중요한 동작 변경)
- Cross-team feature coordination (팀 간 협업 기능)
- Complex UX/flow changes (복잡한 UX/플로우)

If a decision is architectural or long-term, add an ADR in `meta/decisions/` and link it here.

---

## File Naming | 파일 네이밍

Choose one of these patterns and keep it consistent:

- `NNNN-feature-name.md` (e.g., `0007-bulk-export.md`)
- `YYYY-MM-DD-feature-name.md` (e.g., `2026-01-15-bulk-export.md`)

---

## Status Flow | 상태 흐름

- Draft -> Review -> Approved -> In Progress -> Done -> Deprecated

---

## Folder Structure | 폴더 구조

```
docs/planning/
├── index.md                   # [YOU ARE HERE] Navigation + registry
├── feature-plan-template.md   # Detailed planning template
└── NNNN-your-feature.md       # Your planning documents
```

---

## How AI Should Use This | AI 작성 흐름

1. Copy `feature-plan-template.md` to a new file
2. Paste user commands into the "User Command Log" section
3. Fill what you know, and list missing info in "Question Backlog"
4. Ask the user high-priority questions, then update the doc
5. Mark assumptions explicitly if the user does not answer

---

## Planning Docs Registry | 문서 목록

Keep this table updated as you add planning documents.

| Date | Doc | Status | Owner | Notes |
|------|-----|--------|-------|-------|
| YYYY-MM-DD | [NNNN-feature-name](./NNNN-feature-name.md) | Draft | @owner | Short summary |

