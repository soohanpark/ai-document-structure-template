# AI-Powered Development Documentation Template

<!-- TEMPLATE: When using this template, replace this entire section with your project info -->
<!-- TEMPLATE: 이 템플릿 사용 시, 이 섹션 전체를 프로젝트 정보로 교체하세요 -->

> **A comprehensive documentation structure optimized for AI-assisted software development**
>
> 🤖 AI 기반 프로그램 개발을 위한 문서 구조 템플릿

---

## What is This?

This is a **documentation template** designed specifically for projects developed with AI assistance (Claude, GPT, Gemini, Copilot, etc.).

### Why This Template Exists

When working with AI agents on software projects, having a well-structured documentation system is crucial:

- **AI agents need context** - CLAUDE.md provides comprehensive project context
- **Humans need clarity** - README.md offers human-friendly introduction
- **Universal compatibility** - AGENTS.md works with any AI agent
- **Knowledge preservation** - Documentation captures decisions and architecture

### What You Get

```text
ai-document-structure-template/
├── CLAUDE.md              # Template for AI-first project context
├── README.md              # Template for human-readable introduction
├── AGENTS.md              # Template for universal AI agent support
│
├── docs/                  # Structured documentation templates
│   ├── index.md           # Documentation hub
│   ├── architecture/      # System design documentation
│   ├── guides/            # How-to guides
│   ├── api/               # API documentation
│   └── examples/          # Usage examples
│
└── meta/                  # Project governance templates
    ├── contributing.md    # Contribution guidelines
    ├── changelog.md       # Version history
    └── decisions/         # Architecture Decision Records
        └── template.md    # ADR template
```

---

## How to Use This Template

### Option 1: AI-Assisted Setup (Recommended) ⭐

> **가장 쉬운 방법!** AI가 질문을 통해 자동으로 템플릿을 설정합니다.

After cloning the template, simply ask your AI assistant:

```text
"TEMPLATE.md를 바탕으로 템플릿 셋업을 해줘"
```

or in English:

```text
"Set up the template based on TEMPLATE.md"
```

**What happens:**

1. AI reads the setup protocol from [TEMPLATE.md](./TEMPLATE.md)
2. AI asks you questions about your project (name, tech stack, purpose, etc.)
3. AI automatically replaces all placeholders and updates documentation
4. AI removes unnecessary files based on your project type
5. Done! Your documentation is ready.

**Questions AI will ask:**

| Required | Question |
|----------|----------|
| Yes | Project name (프로젝트 이름) |
| Yes | GitHub username/org (GitHub 사용자명) |
| Yes | One-sentence description (한 문장 설명) |
| Yes | Tech stack (기술 스택) |
| Yes | Primary use case (주요 용도) |
| No | Target users, project status, package manager, etc. |

---

### Option 2: Clone and Customize (Manual)

```bash
# Clone this template
git clone https://github.com/YOUR-USERNAME/ai-document-structure-template.git my-project

# Navigate to your project
cd my-project

# Remove template git history
rm -rf .git

# Initialize your own repository
git init
```

### Option 3: Use as GitHub Template

1. Click "Use this template" on GitHub
2. Create your new repository
3. Clone your new repository
4. Use AI-assisted setup (Option 1) or manual setup

---

### Manual Setup Steps (if not using AI)

1. **Replace placeholders** in all files:
   - `{{project-name}}` → Your actual project name
   - Fill in all `<!-- TEMPLATE: ... -->` sections
   - Update dates (YYYY-MM-DD format)

2. **Customize CLAUDE.md**:
   - Fill in Project Overview
   - Update Project Structure to match your codebase
   - Define your Code Conventions
   - List your Development Commands

3. **Update README.md**:
   - Replace this template explanation with your project info
   - Keep the "For AI Agents" section

4. **Keep AGENTS.md** mostly as-is (it's designed to be universal)

5. **Fill in docs/** as your project develops

6. **Delete TEMPLATE.md** after setup is complete

---

## Template Files Overview

| File | Purpose | Audience |
|------|---------|----------|
| **CLAUDE.md** | Single source of truth for AI agents | AI Agents (primary: Claude) |
| **README.md** | Human-friendly project introduction | Humans, GitHub visitors |
| **AGENTS.md** | Universal AI agent quick-start | All AI Agents |
| **docs/** | Detailed documentation | Humans & AI Agents |
| **meta/** | Project governance & decisions | Contributors |

---

## Key Features

### 1. AI-First Design

- CLAUDE.md optimized for AI context windows
- Clear navigation for AI agents
- Consistent structure across all documentation

### 2. Human-Friendly

- README.md for GitHub visitors
- Well-organized docs/ directory
- Clear examples and guides

### 3. Universal AI Support

- Works with Claude, GPT, Gemini, Copilot, Cursor, and more
- AGENTS.md provides compatibility layer
- Standard markdown throughout

### 4. Best Practices Built-In

- Architecture Decision Records (ADR)
- Contribution guidelines
- Changelog template
- Code convention documentation

---

## Documentation Structure Explained

### Root Files

- **CLAUDE.md**: Comprehensive context for AI agents (source of truth)
- **README.md**: Entry point for humans
- **AGENTS.md**: Quick reference for any AI agent

### docs/ Directory

Organized by purpose:

- **architecture/**: System design, components, data flow
- **guides/**: Step-by-step how-to guides
- **api/**: API reference and endpoints
- **examples/**: Usage examples and code samples

### meta/ Directory

Project governance:

- **contributing.md**: How to contribute
- **changelog.md**: Version history
- **decisions/**: Architecture Decision Records (ADRs)

---

## Best Practices

### When to Update Documentation

**Update CLAUDE.md when:**

- Project architecture changes
- New major features are added
- Code conventions are modified
- Development commands change

**Update docs/ when:**

- New features need explanation
- API endpoints change
- Common questions arise
- Examples would help users

**Add to meta/decisions/ when:**

- Making significant architectural decisions
- Choosing between alternatives
- Establishing new patterns

---

## For AI Agents Working With This Template

If you're an AI agent helping someone set up this template:

1. **Read CLAUDE.md** to understand the template structure
2. **Ask the user** for their project details (name, purpose, tech stack)
3. **Replace placeholders** systematically across all files
4. **Remove template instructions** after customization is complete
5. **Keep the structure** - it's designed for AI-powered development

---

## Examples of Projects Using This Template

<!-- TEMPLATE: After publishing, add links to projects using this template -->

_No examples yet - be the first to use this template!_

<!-- - [Example Project 1](https://github.com/user/project) - Description -->

---

## Contributing to This Template

This template itself is open for improvements! See [meta/contributing.md](./meta/contributing.md).

Suggestions welcome:

- Better placeholder strategies
- Additional documentation templates
- Multi-language support
- Automation scripts

---

## License

<!-- TEMPLATE: Choose your license -->
MIT License - feel free to use for any project

---

## Credits

Created for AI-powered development workflows.

Inspired by:

- Claude Code development patterns
- Documentation best practices
- Architecture Decision Records (ADR)
- Open source documentation standards

---

> **Ready to start?** Clone this template and ask your AI: "TEMPLATE.md를 바탕으로 템플릿 셋업을 해줘" 🚀
