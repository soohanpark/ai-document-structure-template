# CLAUDE.md - Project Context for {{project-name}}

<!-- TEMPLATE: This is a template file. Replace {{project-name}} with your actual project name -->
<!-- TEMPLATE: 이 파일은 AI 에이전트(Claude, GPT 등)가 읽는 프로젝트의 핵심 문서입니다 -->

> **This is the canonical source of project information.**
> - For human-readable introduction: [README.md](./README.md)
> - For other AI agents: [AGENTS.md](./AGENTS.md)

---

## How to Use This Template

This file is designed to be the **single source of truth** for AI agents working on your codebase.

**Instructions:**
1. Replace `{{project-name}}` throughout this file with your actual project name
2. Fill in all sections marked with `<!-- TEMPLATE: ... -->` comments
3. Replace placeholder text in **Project Overview** and **Quick Context**
4. Update the **Project Structure** tree to match your actual structure
5. Customize **Code Conventions** and **Development Commands** for your project
6. Remove this "How to Use This Template" section when done

---

## Project Overview

<!-- TEMPLATE: Fill in the table below with your project's actual information -->
<!-- TEMPLATE: 프로젝트의 기본 정보를 아래 표에 입력하세요 -->

| Field | Value |
|-------|-------|
| **Name** | {{project-name}} |
| **Purpose** | <!-- TEMPLATE: What problem does this project solve? --> |
| **Tech Stack** | <!-- TEMPLATE: e.g., TypeScript, React, Node.js, PostgreSQL --> |
| **Status** | <!-- TEMPLATE: e.g., In Development, Production, Prototype --> |

---

## Quick Context

<!-- TEMPLATE: Provide a concise summary that AI agents can quickly understand -->
<!-- TEMPLATE: AI가 프로젝트를 빠르게 이해할 수 있도록 핵심 내용을 작성하세요 -->

**What it does**: <!-- TEMPLATE: 1-2 sentence description of what this project does -->

**Primary use case**: <!-- TEMPLATE: Main use case or scenario -->

**Target users**: <!-- TEMPLATE: Who will use this project? -->

---

## Project Structure

<!-- TEMPLATE: Update this tree to match your actual project structure -->
<!-- TEMPLATE: Keep the docs/ and meta/ structure - it's designed for AI-powered development -->

```
{{project-name}}/
├── CLAUDE.md              # [YOU ARE HERE] Primary AI context
├── README.md              # Human-readable introduction
├── AGENTS.md              # Universal AI agent entry point
│
├── docs/                  # Documentation (recommended structure)
│   ├── index.md           # Documentation hub
│   ├── architecture/      # System design docs
│   │   ├── overview.md    # High-level architecture
│   │   ├── components.md  # Component breakdown
│   │   └── data-flow.md   # Data flow diagrams
│   ├── guides/            # How-to guides
│   │   ├── getting-started.md
│   │   ├── configuration.md
│   │   └── troubleshooting.md
│   ├── api/               # API documentation (if applicable)
│   │   ├── reference.md
│   │   └── endpoints.md
│   └── examples/          # Usage examples
│       ├── basic-usage.md
│       └── advanced-usage.md
│
├── meta/                  # Project metadata & governance
│   ├── contributing.md    # Contribution guidelines
│   ├── changelog.md       # Version history
│   └── decisions/         # Architecture Decision Records (ADR)
│       ├── template.md    # ADR template
│       └── 001-*.md       # Your ADRs
│
└── src/                   # <!-- TEMPLATE: Replace with your source directory -->
    └── ...                # <!-- TEMPLATE: Add your actual project structure -->
```

---

## Documentation Index

### Core Documents (Root)

| Document | Purpose | Audience |
|----------|---------|----------|
| [CLAUDE.md](./CLAUDE.md) | Primary source of truth, AI context | AI Agents (Claude) |
| [README.md](./README.md) | Project introduction | Humans, GitHub visitors |
| [AGENTS.md](./AGENTS.md) | Quick-start for AI agents | All AI Agents |

### Documentation (`docs/`)

| Path | Purpose |
|------|---------|
| [docs/index.md](./docs/index.md) | Documentation hub & navigation |
| [docs/architecture/](./docs/architecture/) | System design & architecture |
| [docs/guides/](./docs/guides/) | How-to guides & tutorials |
| [docs/api/](./docs/api/) | API reference & endpoints |
| [docs/examples/](./docs/examples/) | Usage examples |

### Project Metadata (`meta/`)

| Path | Purpose |
|------|---------|
| [meta/contributing.md](./meta/contributing.md) | How to contribute |
| [meta/changelog.md](./meta/changelog.md) | Version history |
| [meta/decisions/](./meta/decisions/) | Architecture Decision Records (ADR) |

---

## Code Conventions

<!-- TEMPLATE: Customize these conventions for your project -->
<!-- TEMPLATE: AI agents will follow these rules when writing code -->

### Naming Conventions
<!-- TEMPLATE: Define your naming conventions. Example provided below: -->
- Files: `kebab-case.ts` <!-- TEMPLATE: e.g., user-service.ts -->
- Classes: `PascalCase` <!-- TEMPLATE: e.g., UserService -->
- Functions/Variables: `camelCase` <!-- TEMPLATE: e.g., getUserById -->
- Constants: `UPPER_SNAKE_CASE` <!-- TEMPLATE: e.g., MAX_RETRY_COUNT -->

### File Organization
<!-- TEMPLATE: Define your project's file organization pattern -->
```
src/
├── index.ts           # Entry point
├── types/             # Type definitions
├── utils/             # Utility functions
├── core/              # Core business logic
└── __tests__/         # Tests alongside source
```

### Import Order
<!-- TEMPLATE: Define import ordering rules for consistency -->
1. External dependencies
2. Internal modules (absolute paths)
3. Relative imports
4. Type imports

### Error Handling
<!-- TEMPLATE: Define error handling conventions -->
- Always handle errors explicitly
- Use typed errors when possible
- Log errors with context

---

## Development Commands

<!-- TEMPLATE: List all essential commands AI agents need to know -->
<!-- TEMPLATE: Replace with your actual commands and package manager (npm/yarn/pnpm/etc) -->

```bash
# Install dependencies
npm install  # <!-- TEMPLATE: or yarn install, pnpm install, etc -->

# Run development
npm run dev

# Run tests
npm test

# Build for production
npm run build

# Lint code
npm run lint

# Type check
npm run typecheck  # <!-- TEMPLATE: Remove if not applicable -->
```

---

## Architecture Summary

<!-- TEMPLATE: Provide a high-level overview of your system architecture -->
<!-- TEMPLATE: This helps AI agents understand the big picture before diving into code -->
<!-- TEMPLATE: 시스템 아키텍처의 개요를 작성하세요 -->

<!-- TEMPLATE: Example:
This is a client-server application using:
- Frontend: React + TypeScript
- Backend: Node.js + Express
- Database: PostgreSQL
- Authentication: JWT tokens
-->

For detailed architecture documentation:
- [Architecture Overview](./docs/architecture/overview.md)
- [Component Breakdown](./docs/architecture/components.md)
- [Data Flow](./docs/architecture/data-flow.md)

---

## Current State

<!-- TEMPLATE: Keep this section updated as development progresses -->
<!-- TEMPLATE: This helps AI agents understand what's done and what's left to do -->

### Implemented
<!-- TEMPLATE: List completed features with checkboxes -->
- [ ] <!-- TEMPLATE: Feature 1 -->
- [ ] <!-- TEMPLATE: Feature 2 -->

### In Progress
<!-- TEMPLATE: List current work items -->
- [ ] <!-- TEMPLATE: Current work item -->

### Known Limitations
<!-- TEMPLATE: Document known issues or limitations -->
- <!-- TEMPLATE: Limitation or known issue -->

---

## Important Files

<!-- TEMPLATE: List critical files AI agents should know about -->
<!-- TEMPLATE: Update paths to match your actual project structure -->

| File | Description |
|------|-------------|
| `src/index.ts` | <!-- TEMPLATE: Application entry point or main file --> |
| `package.json` | Dependencies & scripts |
| <!-- TEMPLATE: Add more --> | <!-- TEMPLATE: Description --> |

---

## Navigation Guide for AI Agents

When working on this codebase:

1. **Understanding the project** → Start here (CLAUDE.md)
2. **Architecture questions** → [docs/architecture/](./docs/architecture/)
3. **How to do X** → [docs/guides/](./docs/guides/)
4. **API details** → [docs/api/](./docs/api/)
5. **Past decisions** → [meta/decisions/](./meta/decisions/)
6. **Contributing** → [meta/contributing.md](./meta/contributing.md)

---

<!-- TEMPLATE: Keep this date updated when making significant changes -->
_Last updated: YYYY-MM-DD_
