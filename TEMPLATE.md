# Template Usage Guide / 템플릿 사용 가이드

> **AI 기반 프로그램 개발을 위한 문서 구조 템플릿**
> **Documentation Structure Template for AI-Powered Development**

---

## AI-Assisted Setup / AI 지원 셋업

> **사용자에게**: "TEMPLATE.md를 바탕으로 템플릿 셋업을 해줘"라고 AI에게 요청하세요.
> **For Users**: Ask your AI assistant "Set up the template based on TEMPLATE.md"

### For AI Agents: Interactive Setup Protocol

When a user asks to set up this template, follow this interactive workflow:

#### Step 1: Gather Basic Information (필수 정보 수집)

Ask the user these questions **one at a time or in small groups**:

```
[REQUIRED QUESTIONS - 필수 질문]

Q1. 프로젝트 이름이 무엇인가요? (What is your project name?)
    예: my-awesome-app, user-auth-service
    → Used for: {{project-name}} placeholder

Q2. GitHub 사용자명 또는 조직명이 무엇인가요? (What is your GitHub username/org?)
    예: mycompany, john-doe
    → Used for: {{owner}} placeholder

Q3. 프로젝트를 한 문장으로 설명해주세요. (Describe your project in one sentence)
    예: "사용자 인증을 처리하는 마이크로서비스"
    → Used for: CLAUDE.md Quick Context, README.md tagline

Q4. 주요 기술 스택은 무엇인가요? (What is your main tech stack?)
    예: TypeScript, Node.js, PostgreSQL
    → Used for: CLAUDE.md Tech Stack section
```

#### Step 2: Gather Project Details (프로젝트 상세 정보)

```
[DETAIL QUESTIONS - 상세 질문]

Q5. 이 프로젝트의 주요 사용 목적은 무엇인가요? (What is the primary use case?)
    예: "REST API 서버", "CLI 도구", "라이브러리", "웹 애플리케이션"
    → Used for: Determining which docs to keep/remove

Q6. 대상 사용자는 누구인가요? (Who are the target users?)
    예: "백엔드 개발자", "데이터 사이언티스트", "일반 사용자"
    → Used for: CLAUDE.md target users

Q7. 프로젝트의 현재 상태는 어떤가요? (What is the current project status?)
    Options:
    - 아이디어 단계 (Idea stage)
    - 초기 개발 (Initial development)
    - MVP 완료 (MVP complete)
    - 프로덕션 (Production ready)
    → Used for: CLAUDE.md Status field
```

#### Step 3: Technical Preferences (기술적 선호도)

```
[OPTIONAL QUESTIONS - 선택 질문]

Q8. 패키지 매니저는 무엇을 사용하나요? (Which package manager?)
    Options: npm, yarn, pnpm, bun, pip, cargo, etc.
    Default: npm
    → Used for: Development commands

Q9. 테스트 프레임워크는 무엇인가요? (What test framework?)
    예: Jest, Vitest, pytest, Go test
    Default: Project default or "TBD"
    → Used for: Development commands

Q10. REST API가 있나요? (Does your project have REST APIs?)
     Yes/No
     → If No: Remove docs/api/endpoints.md
```

#### Step 4: Execute Setup (셋업 실행)

After gathering information, perform these actions:

```
[SETUP ACTIONS - 셋업 작업]

1. Replace all {{project-name}} with user's project name
2. Replace all {{owner}} with user's GitHub username/org
3. Replace all {{repo}} with user's repository name (usually same as project-name)
4. Replace all {{date}} with today's date (YYYY-MM-DD format)

5. Update CLAUDE.md:
   - Fill Project Overview table
   - Fill Quick Context section
   - Update Development Commands for their stack
   - Set project status

6. Update README.md:
   - Update title and tagline
   - Fill overview section
   - Update Quick Start commands

7. Update AGENTS.md:
   - Update project name in summary table

8. Conditional cleanup:
   - If no REST API: Delete docs/api/endpoints.md
   - If CLI tool: Emphasize CLI documentation in api/reference.md

9. Remove or comment out template instructions (<!-- TEMPLATE: --> comments)

10. Delete TEMPLATE.md (or ask user if they want to keep it for reference)
```

#### Step 5: Confirm Completion (완료 확인)

```
[COMPLETION CHECKLIST - 완료 체크리스트]

Show the user what was updated:
- [ ] {{project-name}} → [actual name] (N files updated)
- [ ] {{owner}} → [actual owner] (N files updated)
- [ ] CLAUDE.md: Project overview filled
- [ ] README.md: Title and description updated
- [ ] Unnecessary files removed (if any)

Ask: "추가로 수정하거나 설정할 내용이 있나요?"
     "Is there anything else you'd like to customize?"
```

---

## Quick Setup Questions Summary / 빠른 셋업 질문 요약

| # | Question (EN) | 질문 (KR) | Required |
|---|---------------|-----------|----------|
| 1 | Project name? | 프로젝트 이름? | Yes |
| 2 | GitHub username/org? | GitHub 사용자명/조직? | Yes |
| 3 | One-sentence description? | 한 문장 설명? | Yes |
| 4 | Tech stack? | 기술 스택? | Yes |
| 5 | Primary use case? | 주요 용도? | Yes |
| 6 | Target users? | 대상 사용자? | No |
| 7 | Project status? | 프로젝트 상태? | No |
| 8 | Package manager? | 패키지 매니저? | No |
| 9 | Test framework? | 테스트 프레임워크? | No |
| 10 | Has REST APIs? | REST API 있음? | No |

---

## Manual Setup / 수동 셋업

If you prefer to set up manually without AI assistance:

### Option 1: GitHub Template (Recommended)

```bash
# Click "Use this template" on GitHub, then clone your new repository
git clone https://github.com/{{your-username}}/{{your-project-name}}.git
cd {{your-project-name}}
```

### Option 2: Manual Clone

```bash
# Clone the template
git clone https://github.com/soohanlee/ai-document-structure-template.git {{your-project-name}}
cd {{your-project-name}}

# Remove template git history and start fresh
rm -rf .git
git init
git add .
git commit -m "Initial commit from AI documentation template"
```

### Placeholder Replacement Commands

```bash
# macOS/Linux - Replace placeholders
find . -type f -name "*.md" -exec sed -i '' 's/{{project-name}}/your-project-name/g' {} +
find . -type f -name "*.md" -exec sed -i '' 's/{{owner}}/your-username/g' {} +
find . -type f -name "*.md" -exec sed -i '' 's/{{repo}}/your-repo-name/g' {} +
find . -type f -name "*.md" -exec sed -i '' 's/{{date}}/2026-01-20/g' {} +
```

---

## Setup Checklist / 설정 체크리스트

### Step 1: Replace Placeholders / 플레이스홀더 교체

| Placeholder | Replace With | Example |
|-------------|--------------|---------|
| `{{project-name}}` | Your project name | `my-awesome-app` |
| `{{owner}}` | GitHub username/org | `mycompany` |
| `{{repo}}` | Repository name | `my-awesome-app` |
| `{{date}}` | Current date | `2026-01-20` |

### Step 2: Update Core Files / 핵심 파일 업데이트

| Priority | File | Action |
|----------|------|--------|
| 1 | `CLAUDE.md` | Fill in project overview, tech stack, purpose |
| 2 | `README.md` | Update project description, features |
| 3 | `AGENTS.md` | Minimal changes needed (mostly auto-updates) |

### Step 3: Customize Documentation / 문서 커스터마이징

| Folder | When to Fill | Priority |
|--------|--------------|----------|
| `docs/architecture/` | After initial design | High |
| `docs/guides/` | When project is runnable | High |
| `docs/api/` | When APIs are stable | Medium |
| `docs/examples/` | When APIs are documented | Medium |
| `meta/` | Ongoing | Low |

### Step 4: Remove Template Artifacts / 템플릿 아티팩트 제거

```bash
# Remove this file after setup
rm TEMPLATE.md

# Optional: Remove template comments from files
# These comments start with <!-- TEMPLATE: -->
```

---

## File-by-File Customization Guide / 파일별 커스터마이징 가이드

### Root Files / 루트 파일

#### `CLAUDE.md` (Primary - Start Here)

This is the main file AI agents read. Fill in:

1. **Project Overview table** - Name, purpose, tech stack, status
2. **Quick Context section** - What it does, use case, target users
3. **Code Conventions** - Keep or modify based on your tech stack
4. **Development Commands** - Update for your package manager/build system
5. **Architecture Summary** - High-level description
6. **Current State** - What's implemented, in progress, known limitations

#### `README.md`

Update for human readers:

1. **Tagline** - One-line description
2. **Overview** - What and why
3. **Quick Start** - Installation and run commands
4. **Features** - Key features list
5. **License** - Your chosen license

#### `AGENTS.md`

Minimal updates needed:

1. **Project Summary table** - Name only (purpose links to CLAUDE.md)
2. **Key Commands** - Update for your stack

---

### Documentation Files / 문서 파일

#### `docs/architecture/`

| File | What to Document |
|------|------------------|
| `overview.md` | System diagram, key components, design principles, technology choices |
| `components.md` | Detailed component docs with interfaces, dependencies, usage |
| `data-flow.md` | How data moves through the system, flow diagrams, data types |

**When to write:** After initial architecture decisions are made.

#### `docs/guides/`

| File | What to Document |
|------|------------------|
| `getting-started.md` | Prerequisites, installation, verification |
| `configuration.md` | Environment variables, config files, deployment settings |
| `troubleshooting.md` | Common issues, diagnostic commands, solutions |

**When to write:** When the project is runnable by others.

#### `docs/api/`

| File | What to Document |
|------|------------------|
| `reference.md` | Functions, classes, types, error handling |
| `endpoints.md` | REST endpoints (if applicable), webhooks, rate limits |

**When to write:** When APIs are stable enough to document.

**Note:** Delete `endpoints.md` if your project doesn't have HTTP APIs.

#### `docs/examples/`

| File | What to Document |
|------|------------------|
| `basic-usage.md` | Hello world, simple patterns, quick wins |
| `advanced-usage.md` | Complex integrations, performance tuning, production patterns |

**When to write:** After API documentation is complete.

---

### Meta Files / 메타 파일

#### `meta/contributing.md`

Customize:

- Development workflow for your team
- Branch naming conventions
- PR review process
- Issue templates

#### `meta/changelog.md`

Maintain as you release:

- Follow Keep a Changelog format
- Update version links at bottom

#### `meta/decisions/`

Create ADRs for significant decisions:

1. Copy `template.md` to `NNN-title.md`
2. Fill in context, decision, consequences
3. Reference from related documentation

---

## Template Philosophy / 템플릿 철학

### Why This Structure? / 왜 이 구조인가?

```text
CLAUDE.md (Source of Truth / 진실의 원천)
    │
    ├─── README.md (Human-friendly intro / 사람 친화적 소개)
    │
    ├─── AGENTS.md (AI agent quick-start / AI 에이전트 빠른 시작)
    │
    ├─── docs/ (Detailed documentation / 상세 문서)
    │     ├── architecture/ (System design / 시스템 설계)
    │     ├── guides/ (How-to / 방법 가이드)
    │     ├── api/ (API reference / API 레퍼런스)
    │     └── examples/ (Usage examples / 사용 예제)
    │
    └─── meta/ (Project governance / 프로젝트 거버넌스)
          ├── contributing.md
          ├── changelog.md
          └── decisions/ (ADRs)
```

### Key Principles / 핵심 원칙

1. **Single Source of Truth** - CLAUDE.md is the index, everything links back to it
2. **AI-First Design** - Structure optimized for AI agents to navigate and understand
3. **Human-Friendly** - README.md provides traditional project introduction
4. **Progressive Disclosure** - Start simple (CLAUDE.md), dive deeper (docs/)
5. **Decision History** - ADRs capture why decisions were made

### For AI Agents / AI 에이전트를 위한 안내

When working with projects using this template:

1. **Start with CLAUDE.md** - Contains project overview and navigation
2. **Check AGENTS.md** - Quick reference and commands
3. **Navigate by need**:
   - Architecture questions → `docs/architecture/`
   - How-to questions → `docs/guides/`
   - API details → `docs/api/`
   - Examples → `docs/examples/`
   - Past decisions → `meta/decisions/`

---

## Best Practices / 모범 사례

### Do's / 해야 할 것

- [ ] Fill CLAUDE.md first - it's the foundation
- [ ] Keep documentation in sync with code changes
- [ ] Use ADRs for significant technical decisions
- [ ] Include working code examples
- [ ] Update changelog with each release

### Don'ts / 하지 말아야 할 것

- [ ] Don't leave placeholder text in production docs
- [ ] Don't duplicate information across files (link instead)
- [ ] Don't write documentation that only humans can understand
- [ ] Don't forget to update CLAUDE.md when architecture changes

---

## FAQ / 자주 묻는 질문

### Q: AI에게 셋업을 요청하려면 어떻게 하나요?

**A:** AI 어시스턴트에게 다음과 같이 요청하세요:
- "TEMPLATE.md를 바탕으로 템플릿 셋업을 해줘"
- "Set up this template for my project"
- "Help me configure this documentation template"

AI가 필요한 정보를 질문하며 자동으로 설정해줍니다.

### Q: Do I need all these files?

**A:** Start with CLAUDE.md, README.md, and AGENTS.md. Add docs/ files as your project grows. Delete unused files (e.g., `endpoints.md` if no REST API).

### Q: How often should I update documentation?

**A:** Update CLAUDE.md whenever architecture changes. Update guides when workflows change. Update API docs when interfaces change.

### Q: Can I use a different documentation tool?

**A:** Yes! This structure works with tools like Docusaurus, MkDocs, or GitBook. The markdown files serve as the source.

### Q: What if my project doesn't use TypeScript?

**A:** Replace TypeScript examples with your language. The structure remains the same.

---

## Getting Help / 도움 받기

- **AI Assistant**: Ask "Help me set up this template" or "TEMPLATE.md 기반으로 셋업해줘"
- **Issues**: Report problems or request features
- **Discussions**: Ask questions about using the template
- **Contributions**: See `meta/contributing.md` for guidelines

---

_After setup, delete this file (`TEMPLATE.md`) from your project._
