# Documentation Hub Template

> **템플릿 사용 가이드 | Template Usage Guide**
>
> This is a template for organizing your project documentation. Replace all placeholder text with your project-specific content.
>
> 이 파일은 프로젝트 문서화를 위한 템플릿입니다. 모든 플레이스홀더를 프로젝트에 맞게 수정하세요.
>
> **Source of Truth**: [CLAUDE.md](../CLAUDE.md)

---

## Documentation Structure

**What this structure provides | 이 구조가 제공하는 것:**
- Clear navigation for both humans and AI agents
- Logical separation of concerns (architecture vs guides vs API)
- Consistent location for different types of documentation

```
docs/
├── index.md           # [YOU ARE HERE] Documentation navigation hub
├── architecture/      # System design & technical architecture
├── guides/            # Step-by-step how-to guides
├── planning/          # Feature planning & product specs
├── api/               # API reference & specifications
└── examples/          # Usage examples & tutorials
```

---

## Quick Navigation

### Architecture | 아키텍처

**What to document here | 여기에 작성할 내용:**
- System design and technical decisions
- Component relationships and responsibilities
- Data flow and state management
- Technology choices and rationale

**시스템 설계 및 기술적 의사결정을 문서화하세요.**

| Document | Description | 설명 |
|----------|-------------|------|
| [architecture/overview.md](./architecture/overview.md) | High-level architecture | 고수준 아키텍처 개요 |
| [architecture/components.md](./architecture/components.md) | Component breakdown | 컴포넌트별 상세 설명 |
| [architecture/data-flow.md](./architecture/data-flow.md) | Data flow diagrams | 데이터 흐름 및 상태 관리 |

### Guides | 가이드

**What to document here | 여기에 작성할 내용:**
- Step-by-step setup instructions
- Configuration options and environment setup
- Common workflows and best practices
- Troubleshooting common issues

**단계별 설명, 설정 방법, 문제 해결 가이드를 작성하세요.**

| Document | Description | 설명 |
|----------|-------------|------|
| [guides/getting-started.md](./guides/getting-started.md) | First-time setup | 초기 설정 및 시작 가이드 |
| [guides/configuration.md](./guides/configuration.md) | Configuration options | 설정 옵션 및 환경 구성 |
| [guides/troubleshooting.md](./guides/troubleshooting.md) | Common issues & solutions | 일반적인 문제 및 해결 방법 |

### Planning | 기획

**What to document here | 여기에 작성할 내용:**
- Feature planning documents and product specs
- Problem statements, goals, scope, and acceptance criteria
- AI-authored drafts based on user commands

**기능 기획서, 요구사항, 스펙 문서를 작성하세요.**

| Document | Description | 설명 |
|----------|-------------|------|
| [planning/index.md](./planning/index.md) | Planning docs hub | 기획 문서 허브 |
| [planning/feature-plan-template.md](./planning/feature-plan-template.md) | Feature planning template | 기능 기획 템플릿 |

### API Reference | API 레퍼런스

**What to document here | 여기에 작성할 내용:**
- Complete API specifications
- Endpoint documentation (methods, parameters, responses)
- Authentication and authorization
- Request/response examples

**API 명세, 엔드포인트 문서, 인증 방식을 작성하세요.**

| Document | Description | 설명 |
|----------|-------------|------|
| [api/reference.md](./api/reference.md) | Complete API reference | 전체 API 레퍼런스 |
| [api/endpoints.md](./api/endpoints.md) | Endpoint specifications | 엔드포인트별 상세 명세 |

### Examples | 예제

**What to document here | 여기에 작성할 내용:**
- Simple usage examples for beginners
- Complex scenarios and advanced patterns
- Code snippets with explanations
- Real-world use cases

**초보자를 위한 기본 예제와 고급 사용 사례를 작성하세요.**

| Document | Description | 설명 |
|----------|-------------|------|
| [examples/basic-usage.md](./examples/basic-usage.md) | Simple use cases | 기본 사용 예제 |
| [examples/advanced-usage.md](./examples/advanced-usage.md) | Complex scenarios | 고급 사용 패턴 |

---

## Related Documentation

**How AI agents navigate | AI 에이전트 탐색 방식:**
- **CLAUDE.md**: Primary context and source of truth
- **AGENTS.md**: Quick-start entry point
- **docs/**: Detailed technical documentation
- **meta/**: Governance and decision records

| Location | Content | 내용 |
|----------|---------|------|
| [../CLAUDE.md](../CLAUDE.md) | Project context (source of truth) | 프로젝트 컨텍스트 (주 정보원) |
| [../README.md](../README.md) | Project introduction | 프로젝트 소개 |
| [../AGENTS.md](../AGENTS.md) | AI agent quick-start | AI 에이전트 진입점 |
| [../meta/](../meta/) | Project metadata & governance | 프로젝트 메타데이터 및 거버넌스 |

---

## How to Use This Template

**For new projects | 새 프로젝트에서:**

1. Replace all placeholder content with your project details
2. Delete sections that don't apply to your project
3. Add new sections specific to your domain
4. Update links as you create new documentation files
5. Keep the structure consistent for AI agent navigation

**For AI agents | AI 에이전트를 위한 안내:**

- Start at [CLAUDE.md](../CLAUDE.md) for project context
- Use this hub to navigate to specific documentation areas
- Architecture docs explain "why" and "how it works"
- Guides explain "how to do X"
- API docs explain "what endpoints/functions exist"
- Examples show "working code"

---

## Contributing to Docs

See [../meta/contributing.md](../meta/contributing.md) for documentation contribution guidelines.

**문서 작성 가이드는 [../meta/contributing.md](../meta/contributing.md)를 참고하세요.**
