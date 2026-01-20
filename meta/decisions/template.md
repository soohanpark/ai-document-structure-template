# ADR Template

> **TEMPLATE INSTRUCTIONS**
>
> Architecture Decision Records (ADRs) capture important architectural decisions.
>
> **When to create an ADR**:
> - Changing core architecture or design patterns
> - Adopting or removing major dependencies/frameworks
> - Making significant technology choices
> - Changing data models or API contracts
> - Decisions with long-term impact or that are hard to reverse
> - Trade-offs between multiple valid approaches
>
> **When NOT to create an ADR**:
> - Minor code refactoring
> - Bug fixes (unless they reveal architectural issues)
> - Routine dependency updates
> - Documentation improvements
> - Trivial configuration changes
>
> **How to use this template**:
> 1. Copy this file to `NNN-title-in-kebab-case.md` (sequential number)
> 2. Replace placeholders with actual content
> 3. Fill in all sections thoroughly
> 4. Include in your PR with the implementation
> 5. Update CLAUDE.md if the decision affects AI context
>
> **ADR이란 (Korean)**:
> - Architecture Decision Record: 중요한 아키텍처 결정을 기록
> - 왜 이 결정을 했는지, 어떤 대안을 고려했는지 문서화
> - AI 에이전트가 과거 결정의 맥락을 이해하는 데 도움
>
> **ADR 작성 시기**:
> - 핵심 아키텍처 변경
> - 주요 기술 스택 선택
> - 데이터 모델 변경
> - API 계약 변경
> - 장기적 영향이 있는 결정

---

# [NUMBER]. [TITLE]

> _Replace [NUMBER] with sequential number (e.g., 002, 003)_
> _Replace [TITLE] with decision title (e.g., "Switch to PostgreSQL")_

**Date**: YYYY-MM-DD

**Status**: [Proposed | Accepted | Deprecated | Superseded by [ADR-NNN](./NNN-link.md)]

**Decision makers**: _[Who was involved in this decision?]_

**Tags**: `#architecture` `#database` `#api` _(add relevant tags)_

---

## Summary

> **TL;DR for AI agents and quick readers**

_One paragraph summary: What decision was made and why?_

**Example**: "We decided to switch from MongoDB to PostgreSQL for our primary database because we need strong transaction guarantees and complex relational queries. This change will require data migration but provides better data integrity."

---

## Context

> **What problem are we solving?**

_Describe the issue, requirement, or context that is motivating this decision:_

- What problem exists?
- What constraints do we have?
- What requirements must be met?
- What triggered this decision?

**Questions to answer**:
- What is the business/technical context?
- What are we trying to achieve?
- What are the current pain points?
- What requirements or constraints exist?

**Example**:
```
Our application currently uses MongoDB, but we're experiencing:
- Data consistency issues due to lack of ACID transactions
- Difficulty expressing complex relational queries
- Challenges with schema evolution and validation

We need a database that supports:
- Strong consistency guarantees
- Complex JOIN operations
- Schema migrations
- ACID transactions
```

---

## Decision

> **What are we doing?**

_Describe the decision and how it will be implemented:_

- What specifically are we changing?
- How will it be implemented?
- What is the scope of this change?
- What is the timeline?

**Be specific and actionable.**

**Example**:
```
We will migrate from MongoDB to PostgreSQL:

1. Set up PostgreSQL cluster with primary and replica
2. Design relational schema based on current data model
3. Implement data migration scripts
4. Update ORM layer to use PostgreSQL driver
5. Migrate production data during maintenance window
6. Keep MongoDB as read-only backup for 3 months
```

---

## Consequences

> **What happens as a result?**

### Positive

- _[Positive consequence 1]_
- _[Positive consequence 2]_
- _[Positive consequence 3]_

**Examples**:
- Strong ACID guarantees improve data integrity
- Complex queries become simpler with SQL JOINs
- Better tooling and ecosystem support
- Mature replication and backup solutions

### Negative

- _[Negative consequence 1]_
- _[Negative consequence 2]_
- _[Negative consequence 3]_

**Examples**:
- One-time migration effort required (estimated 2 weeks)
- Need to learn PostgreSQL-specific features
- Horizontal scaling is more complex than with MongoDB
- Costs increase due to managed PostgreSQL pricing

### Neutral

- _[Neutral consequence - neither good nor bad, just a change]_

**Examples**:
- Team needs training on PostgreSQL
- Different backup procedures
- New monitoring dashboards required

---

## Alternatives Considered

> **What else did we think about?**

### Alternative 1: _[Name of alternative]_

**Description**: _[Brief description of this alternative]_

**Pros**:
- _[Advantage 1]_
- _[Advantage 2]_

**Cons**:
- _[Disadvantage 1]_
- _[Disadvantage 2]_

**Why not chosen**: _[Explain why this wasn't selected]_

---

### Alternative 2: _[Name of alternative]_

**Description**: _[Brief description of this alternative]_

**Pros**:
- _[Advantage 1]_
- _[Advantage 2]_

**Cons**:
- _[Disadvantage 1]_
- _[Disadvantage 2]_

**Why not chosen**: _[Explain why this wasn't selected]_

---

### Alternative 3: Do Nothing

**Description**: _[Keep current approach]_

**Pros**:
- _[No migration cost]_
- _[No disruption]_

**Cons**:
- _[Problem persists]_
- _[Technical debt grows]_

**Why not chosen**: _[Why status quo is not acceptable]_

---

## Implementation Plan

> **How will we execute this decision?** (Optional but recommended)

### Phase 1: Preparation
- [ ] _[Task 1]_
- [ ] _[Task 2]_

### Phase 2: Implementation
- [ ] _[Task 1]_
- [ ] _[Task 2]_

### Phase 3: Validation
- [ ] _[Task 1]_
- [ ] _[Task 2]_

**Timeline**: _[Estimated completion date]_

**Success criteria**: _[How do we know this succeeded?]_

---

## Risks and Mitigation

> **What could go wrong?** (Optional but recommended)

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| _[Risk 1]_ | High/Medium/Low | High/Medium/Low | _[How to mitigate]_ |
| _[Risk 2]_ | High/Medium/Low | High/Medium/Low | _[How to mitigate]_ |

**Example**:
| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| Data loss during migration | High | Low | Test migration on staging, keep MongoDB backup for 3 months |
| Performance degradation | Medium | Medium | Load testing before production, rollback plan ready |

---

## References

> **Related resources**

**Documentation**:
- _[Link to relevant documentation]_
- _[Link to design doc]_

**Related ADRs**:
- _[Link to related ADR]_
- _[Link to superseded ADR]_

**External Resources**:
- _[Link to article, RFC, or external documentation]_
- _[Link to benchmark or case study]_

**Issues/PRs**:
- _[GitHub issue #XXX]_
- _[Pull Request #XXX]_

---

## Notes

> **Additional context for future readers** (Optional)

_Any additional information that doesn't fit above but would be helpful:_
- Historical context
- Lessons learned
- Follow-up items
- Related discussions

---

## For AI Agents

> **AI Context** (Optional - helps AI understand the decision)

**Impact on codebase**:
- _[Which modules/components are affected?]_
- _[What patterns should AI look for?]_
- _[What should AI avoid doing?]_

**Related patterns**:
- _[Coding patterns introduced by this decision]_
- _[Anti-patterns to avoid]_

---

## Customization Checklist

**Before submitting this ADR**:

- [ ] Replace [NUMBER] with next sequential number
- [ ] Replace [TITLE] with descriptive title
- [ ] Fill in Date, Status, Decision makers
- [ ] Add relevant tags
- [ ] Write clear Summary
- [ ] Complete Context section
- [ ] Detail Decision section
- [ ] List all Consequences (positive, negative, neutral)
- [ ] Document at least 2 Alternatives Considered
- [ ] Add References
- [ ] Remove placeholder examples
- [ ] Remove this checklist
- [ ] Review for clarity and completeness

---

_ADR Template Version: 1.0.0_
_Last updated: {{date}}_
