# Feature Planning Document Template

> **TEMPLATE INSTRUCTIONS | 템플릿 안내**
>
> This document is meant to be drafted by AI based on user commands.
> If required information is missing, the AI should ask questions and record answers.
> Remove or replace all placeholder text before approval.
>
> 이 문서는 AI가 사용자 명령을 바탕으로 초안을 작성하도록 설계되었습니다.
> 필수 정보가 부족하면 질문하고, 답변을 기록하세요.
> 최종 승인 전 템플릿 문구를 모두 제거하세요.

---

## Document Metadata | 문서 메타데이터

| Field | Value |
|-------|-------|
| **Doc ID** | NNNN-feature-name |
| **Feature Name** | <!-- Example: Bulk Export --> |
| **Status** | Draft / Review / Approved / In Progress / Done / Deprecated |
| **Owner** | @owner |
| **Stakeholders** | @pm, @design, @engineering |
| **Created** | YYYY-MM-DD |
| **Last Updated** | YYYY-MM-DD |
| **Target Release** | <!-- e.g., 2026-Q1 --> |
| **Related ADRs** | <!-- Link ADRs if architectural decisions are needed --> |
| **Related Issues/PRs** | <!-- Links --> |

---

## AI Authoring Guide | AI 작성 가이드

### How to Draft | 작성 흐름

1. Paste the user commands into "User Command Log"
2. Fill a minimal draft: Summary, Problem, Goals, Scope
3. List missing info in "Question Backlog" and ask the user
4. Update the doc with answers, or mark assumptions explicitly
5. Keep all decisions and changes in "Decision Log"

### Required Inputs Checklist | 필수 입력 체크리스트

- Problem statement (문제 정의)
- Target users/personas (대상 사용자)
- Goals and non-goals (목표/비목표)
- Scope boundaries (스코프)
- Success metrics (성공 지표)
- Functional requirements (기능 요구사항)
- Non-functional requirements (비기능 요구사항)
- Risks and rollout (리스크, 배포 계획)

### Question Backlog | 질문 백로그

| ID | Question | Why Needed | Priority | Answer | Status |
|----|----------|------------|----------|--------|--------|
| Q1 | <!-- Ask here --> | <!-- Context --> | High/Med/Low | <!-- Answer --> | Open/Answered |

### Assumptions & Constraints | 가정 및 제약

| ID | Assumption/Constraint | Reason | Risk |
|----|------------------------|--------|------|
| A1 | <!-- Example: No new backend service --> | <!-- Why --> | Low/Med/High |

### Decision Log | 결정 로그

| Date | Decision | Reason | Owner |
|------|----------|--------|-------|
| YYYY-MM-DD | <!-- Decision --> | <!-- Why --> | @owner |

---

## User Command Log | 사용자 명령 기록

| Date | Command | Interpretation | Notes |
|------|---------|----------------|------|
| YYYY-MM-DD | "..." | <!-- AI paraphrase --> | <!-- Context --> |

---

## 1. Summary | 요약

**TL;DR**: <!-- 2-3 sentences: what we are building and why -->

**One-line value**: <!-- Example: Enable admins to export reports in CSV within 2 clicks -->

---

## 2. Background & Problem | 배경과 문제

### Current Situation | 현재 상황
- <!-- What happens today? -->
- <!-- Pain points and evidence -->

### Problem Statement | 문제 정의
- <!-- Clear, measurable problem -->

### Root Causes (Optional) | 근본 원인 (선택)
- <!-- If known, list the causes -->

---

## 3. Goals & Non-Goals | 목표와 비목표

### Goals | 목표
- G1: <!-- Goal statement -->
- G2: <!-- Goal statement -->

### Non-Goals | 비목표
- NG1: <!-- Out of scope -->
- NG2: <!-- Out of scope -->

---

## 4. Success Metrics | 성공 지표

| Metric | Baseline | Target | How Measured | Owner |
|--------|----------|--------|--------------|-------|
| <!-- e.g., Export success rate --> | <!-- % --> | <!-- % --> | <!-- Source --> | @owner |

---

## 5. Scope | 스코프

### In Scope | 포함
- <!-- Must-have items -->

### Out of Scope | 제외
- <!-- Explicit exclusions -->

### Dependencies | 의존성
- <!-- Internal teams, APIs, data sources -->

---

## 6. Stakeholders | 이해관계자

| Role | Name | Responsibility | Notes |
|------|------|----------------|-------|
| PM | @pm | Product direction | |
| Design | @design | UX/UI | |
| Engineering | @eng | Implementation | |
| Data/Analytics | @data | Metrics | |

---

## 7. Users & Personas | 사용자 및 페르소나

### Primary Users | 주요 사용자
- Persona A: <!-- Who, goals, pain points -->

### Secondary Users | 보조 사용자
- Persona B: <!-- Who, goals, pain points -->

### User Scenarios | 사용자 시나리오
1. <!-- Scenario 1 step-by-step -->
2. <!-- Scenario 2 step-by-step -->

---

## 8. User Journey & UX Flow | 사용자 여정 및 UX 흐름

### Journey Steps | 여정 단계
1. <!-- Entry point -->
2. <!-- Action -->
3. <!-- Outcome -->

### UX States | 상태
- Empty state:
- Loading state:
- Error state:
- Permission/blocked state:
- Success state:

### Copy & Messaging | 문구
- Primary CTA:
- Error messages:
- Helper text:

---

## 9. Functional Requirements | 기능 요구사항

| ID | Requirement | Priority | Acceptance Criteria | Notes |
|----|-------------|----------|---------------------|-------|
| FR-1 | <!-- Requirement --> | High/Med/Low | <!-- Testable criteria --> | |
| FR-2 | <!-- Requirement --> | High/Med/Low | <!-- Testable criteria --> | |

---

## 10. Non-Functional Requirements | 비기능 요구사항

### Performance | 성능
- <!-- Latency, throughput, concurrency targets -->

### Reliability | 안정성
- <!-- Availability, retry policy, SLA -->

### Security & Privacy | 보안 및 개인정보
- <!-- Auth, data protection, retention -->

### Compliance | 준수 사항
- <!-- Legal/regulatory constraints -->

### Accessibility | 접근성
- <!-- WCAG targets, keyboard support -->

### Internationalization | 다국어/지역화
- <!-- Locale support, formatting -->

---

## 11. Data Model | 데이터 모델

### Entities | 엔티티
- Entity A
  - Fields: <!-- field, type, constraints -->
  - Validation: <!-- rules -->

### Relationships | 관계
- <!-- Relationships and cardinality -->

### Data Lifecycle | 데이터 수명
- Creation:
- Update:
- Deletion:
- Retention:

---

## 12. API / Integrations | API 및 통합

### Internal APIs | 내부 API
- Endpoint: `METHOD /path`
  - Request:
  - Response:
  - Errors:

### External Integrations | 외부 통합
- Service: <!-- Name -->
  - Purpose:
  - Auth:
  - Limits:

### Events / Webhooks | 이벤트/웹훅
- Event name:
  - Trigger:
  - Payload:

---

## 13. Permissions & Roles | 권한 및 역할

- Roles:
  - Admin:
  - Member:
  - Viewer:
- Access rules:
  - <!-- Who can view/create/edit/delete -->

---

## 14. Analytics & Logging | 분석 및 로깅

### Events | 이벤트
- `event_name` - when/why it fires

### Dashboards | 대시보드
- <!-- Key charts and owners -->

### Logging | 로그
- <!-- Key logs and redaction rules -->

---

## 15. Rollout & Migration | 배포 및 마이그레이션

### Rollout Plan | 배포 계획
- Feature flag: <!-- Yes/No -->
- Phased rollout: <!-- % or segments -->
- Rollback plan:

### Migration | 마이그레이션
- Data backfill:
- Compatibility:
- Downtime expectations:

---

## 16. Testing Strategy | 테스트 전략

- Unit tests:
- Integration tests:
- E2E tests:
- Load tests:
- Security tests:

---

## 17. Risks & Mitigations | 리스크 및 대응

| Risk | Impact | Probability | Mitigation | Owner |
|------|--------|-------------|------------|-------|
| <!-- Risk --> | High/Med/Low | High/Med/Low | <!-- Plan --> | @owner |

---

## 18. Alternatives Considered | 고려한 대안

- Alternative A:
  - Pros:
  - Cons:
  - Why not chosen:

---

## 19. Timeline & Milestones | 일정 및 마일스톤

| Milestone | Date | Owner | Notes |
|-----------|------|-------|-------|
| <!-- Example: Design complete --> | YYYY-MM-DD | @owner | |

---

## 20. Open Questions | 미해결 질문

- Q1:
- Q2:

---

## 21. Appendix | 부록

- Links to mockups, tickets, docs
- Related research or user feedback

---

## Customization Checklist | 최종 체크리스트

- [ ] Replace all placeholders
- [ ] Answer all high-priority questions
- [ ] Validate acceptance criteria for FRs
- [ ] Confirm success metrics and ownership
- [ ] Link related ADRs or decisions
- [ ] Remove template instructions

