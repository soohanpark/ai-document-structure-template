# AGENTS.md - AI Agent Quick Start

<!-- TEMPLATE: This file is designed to remain mostly unchanged when using the template -->
<!-- TEMPLATE: Only update the Project Summary table and Key Commands section -->
<!-- TEMPLATE: 이 파일은 템플릿 사용 시 대부분 그대로 유지하세요 -->

> **Universal entry point for AI agents** (Claude, GPT, Gemini, Copilot, Cursor, etc.)

---

## Primary Context Source

> **Read [CLAUDE.md](./CLAUDE.md) first** - it contains complete project context.

This file provides a quick reference. For full details, always refer to CLAUDE.md.

---

## Quick Reference

### Project Summary

<!-- TEMPLATE: Update this table to match your project -->
<!-- TEMPLATE: Keep it minimal - detailed info belongs in CLAUDE.md -->

| Field | Value |
|-------|-------|
| **Name** | {{project-name}} |
| **Purpose** | <!-- TEMPLATE: One-line description (or "See CLAUDE.md") --> |
| **Tech Stack** | <!-- TEMPLATE: Main technologies (or "See CLAUDE.md") --> |

### Key Commands

<!-- TEMPLATE: Update these commands to match your actual project -->
<!-- TEMPLATE: Replace npm with yarn/pnpm if applicable -->

```bash
npm install    # Install dependencies
npm run dev    # Development mode
npm test       # Run tests
npm run build  # Production build
npm run lint   # Lint code
```

### Important Paths

<!-- TEMPLATE: Update paths to match your project structure -->

| Path | Description |
|------|-------------|
| `src/` | <!-- TEMPLATE: Main source code directory --> |
| `tests/` | <!-- TEMPLATE: Test files (or __tests__, spec/, etc.) --> |
| `docs/` | Documentation |
| `meta/` | Project metadata |

---

## Before Making Changes

<!-- TEMPLATE: This section is universal - keep as-is -->

1. **Read [CLAUDE.md](./CLAUDE.md)** for full project context
2. **Check [meta/decisions/](./meta/decisions/)** for architectural decisions
3. **Follow conventions** defined in CLAUDE.md
4. **Run tests** before committing

---

## Documentation Map

<!-- TEMPLATE: This structure is universal - keep as-is -->

```
CLAUDE.md (START HERE)
    │
    ├── docs/
    │   ├── architecture/  → System design
    │   ├── guides/        → How-to guides
    │   ├── api/           → API reference (if applicable)
    │   └── examples/      → Usage examples
    │
    └── meta/
        ├── contributing.md → Contribution guide
        ├── changelog.md    → Version history
        └── decisions/      → ADRs
```

### Quick Links

<!-- TEMPLATE: Keep this navigation table as-is -->

| Need | Go To |
|------|-------|
| Project overview | [CLAUDE.md](./CLAUDE.md) |
| Architecture | [docs/architecture/](./docs/architecture/) |
| How-to guides | [docs/guides/](./docs/guides/) |
| API reference | [docs/api/](./docs/api/) |
| Examples | [docs/examples/](./docs/examples/) |
| Contributing | [meta/contributing.md](./meta/contributing.md) |
| Past decisions | [meta/decisions/](./meta/decisions/) |

---

## Agent-Specific Notes

<!-- TEMPLATE: This section is universal - keep as-is -->

### For Claude (Anthropic)
- CLAUDE.md is optimized for your context window
- Start with CLAUDE.md, then dive into specific docs as needed
- The documentation index in CLAUDE.md provides navigation

### For GPT (OpenAI)
- CLAUDE.md uses standard markdown, fully compatible
- Follow the documentation structure in CLAUDE.md
- Check code conventions before making changes

### For Gemini (Google)
- Standard markdown format throughout
- Use CLAUDE.md as your primary reference
- Documentation is organized hierarchically

### For Copilot / Cursor / Other
- CLAUDE.md is the single source of truth
- All documentation uses standard markdown
- Follow the project structure defined in CLAUDE.md

---

## Code Conventions Summary

<!-- TEMPLATE: Update this if your conventions differ significantly -->
<!-- TEMPLATE: Full conventions should be in CLAUDE.md -->

> Full conventions in [CLAUDE.md](./CLAUDE.md)

- **Files**: `kebab-case.ts` <!-- TEMPLATE: Adjust for your language -->
- **Classes**: `PascalCase`
- **Functions/Variables**: `camelCase`
- **Constants**: `UPPER_SNAKE_CASE`

---

## Workflow Checklist

<!-- TEMPLATE: Keep this universal checklist as-is -->

When working on this codebase:

- [ ] Read CLAUDE.md for context
- [ ] Check relevant docs/ for specific guidance
- [ ] Follow code conventions
- [ ] Run tests (`npm test`)
- [ ] Run lint (`npm run lint`)
- [ ] Update docs if needed

---

_This file is designed to be compatible with any AI agent. For the most comprehensive context, always start with [CLAUDE.md](./CLAUDE.md)._
