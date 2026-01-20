# 1. AI-Optimized Documentation Structure for Template Repository

**Date**: 2026-01-14

**Status**: Accepted

**Decision makers**: Template Creator

**Tags**: `#architecture` `#documentation` `#ai-agents` `#template`

---

## Summary

We created a comprehensive documentation structure template optimized for AI-assisted development. This template provides a three-tier documentation system (CLAUDE.md, README.md, AGENTS.md) with hierarchical docs and metadata directories, specifically designed to give AI agents complete project context while remaining human-friendly.

---

## Context

Modern software development increasingly involves AI coding assistants (Claude, GitHub Copilot, Cursor, etc.). However, most project templates lack structured documentation that helps AI agents understand project context, conventions, and architecture.

### Problems with traditional documentation:

1. **README.md as single source** - Gets too long, mixes human and AI concerns
2. **No AI-specific entry point** - AI agents don't know where to start
3. **Poor discoverability** - Related docs scattered, no clear navigation
4. **Missing decision history** - No record of why architectural choices were made
5. **Inconsistent structure** - Each project organizes docs differently

### Requirements:

- Provide comprehensive context for AI agents (especially Claude Code)
- Remain accessible and useful for human developers
- Support multiple AI tools, not just Claude
- Enable easy navigation across all documentation
- Capture architectural decisions and project history
- Be reusable as a template for new projects

---

## Decision

Create a **three-tier documentation template** optimized for AI-assisted development:

### Tier 1: Root-Level Entry Points

**CLAUDE.md** - Primary AI Context File
- Central source of truth for AI agents
- Comprehensive project overview with quick-reference tables
- Links to all other documentation
- AI-optimized format (tables, clear sections, cross-references)
- Contains: Project overview, structure, conventions, current state, navigation guide

**README.md** - Human Introduction
- Friendly introduction for GitHub visitors
- Quick start and basic usage
- Points to CLAUDE.md as the detailed source
- Human-focused, not AI-optimized

**AGENTS.md** - Universal AI Agent Entry Point
- Quick-start for any AI agent (not just Claude)
- Architecture overview, key files, patterns
- Links to CLAUDE.md for full context
- Ensures compatibility with future AI tools

### Tier 2: Documentation Directory (`docs/`)

```
docs/
├── index.md              # Documentation hub
├── architecture/         # System design
│   ├── overview.md
│   ├── components.md
│   └── data-flow.md
├── guides/               # How-to guides
│   ├── getting-started.md
│   ├── configuration.md
│   └── troubleshooting.md
├── api/                  # API reference
│   ├── reference.md
│   └── endpoints.md
└── examples/             # Usage examples
    ├── basic-usage.md
    └── advanced-usage.md
```

### Tier 3: Metadata Directory (`meta/`)

```
meta/
├── contributing.md       # Contribution guidelines
├── changelog.md          # Version history (Keep a Changelog format)
└── decisions/            # Architecture Decision Records
    ├── template.md       # ADR template with guidance
    └── 001-documentation-structure.md  # This document
```

### Cross-Reference Strategy

- **CLAUDE.md** serves as the hub, linking to all documentation
- **README.md** and **AGENTS.md** point to CLAUDE.md for details
- All documents can navigate back to CLAUDE.md for project context
- ADRs reference related documentation and other ADRs
- Documentation includes "For AI Agents" sections where helpful

### Template Features

All documents include:
- Template instructions at the top
- `{{project-name}}`, `{{owner}}`, `{{repo}}` placeholders
- Korean bilingual explanations for key concepts
- Customization checklists
- Clear examples and guidance

---

## Consequences

### Positive

1. **Superior AI agent context** - AI assistants can quickly understand entire project
2. **Human-friendly** - Developers still have familiar README.md entry point
3. **Universal AI support** - Works with Claude, Cursor, GitHub Copilot, etc.
4. **Clear navigation** - Hub-and-spoke model from CLAUDE.md
5. **Decision history** - ADRs capture "why" for future reference
6. **Reusable template** - Can be cloned and customized for any project
7. **Organized structure** - Clear separation: docs/ (documentation), meta/ (governance)
8. **Bilingual support** - Korean explanations help broader audience
9. **Best practices built-in** - Conventional Commits, Keep a Changelog, ADRs

### Negative

1. **Initial setup overhead** - More files to customize than single README
2. **Maintenance burden** - Multiple entry points need to stay synchronized
3. **Learning curve** - New contributors need to understand the structure
4. **More opinionated** - Template enforces specific documentation patterns
5. **Over-documentation risk** - Small projects might find it excessive

### Neutral

1. **Standard markdown** - Widely compatible, no special tools needed
2. **In-repository** - All docs version-controlled with code
3. **Follows conventions** - Based on ADR, Keep a Changelog, Conventional Commits

---

## Alternatives Considered

### Alternative 1: Single README.md

**Description**: Traditional approach with all documentation in README.md

**Pros**:
- Simple, one file to maintain
- Familiar to all developers
- No navigation complexity

**Cons**:
- Becomes too long for real projects (3000+ lines common)
- Mixes human and AI concerns
- Poor discoverability of detailed docs
- No structured AI context

**Why not chosen**: Doesn't scale well and doesn't optimize for AI agents. Large READMEs are hard for both humans and AI to navigate.

---

### Alternative 2: Wiki-based Documentation

**Description**: Use GitHub Wiki or external wiki platform

**Pros**:
- Easy to edit via web interface
- Good search functionality
- Can be extensive without cluttering repo

**Cons**:
- Not version-controlled with code
- Harder for AI agents to access (separate from codebase)
- Can drift out of sync with code
- Requires separate tooling

**Why not chosen**: AI coding assistants work best with in-repository documentation. Wikis are less accessible during AI-assisted development sessions.

---

### Alternative 3: AI-Only Documentation (No Human Focus)

**Description**: Create only CLAUDE.md, optimized purely for AI consumption

**Pros**:
- Maximum AI optimization
- Single source of truth
- No duplication

**Cons**:
- Alienates human developers
- Not friendly for GitHub browsing
- Violates conventions (README.md expected)
- Poor first impression for visitors

**Why not chosen**: Need to serve both humans and AI. README.md is expected on GitHub.

---

### Alternative 4: docs.rs or Dedicated Doc Site

**Description**: Use documentation generator (like Docusaurus, MkDocs, etc.)

**Pros**:
- Beautiful presentation
- Great search
- Versioned docs

**Cons**:
- Requires build/deploy process
- Harder for AI agents to parse (HTML/generated)
- More complex setup
- Overkill for many projects

**Why not chosen**: Adds complexity without improving AI agent access. Markdown in repo is simpler and more AI-friendly.

---

## Implementation Plan

### Phase 1: Template Creation ✅
- [x] Create CLAUDE.md template
- [x] Create README.md template
- [x] Create AGENTS.md template
- [x] Set up docs/ hierarchy
- [x] Set up meta/ hierarchy
- [x] Create ADR template
- [x] Document this decision

### Phase 2: Template Refinement ✅
- [x] Add template instructions to all files
- [x] Add Korean bilingual explanations
- [x] Add customization checklists
- [x] Add examples throughout

### Phase 3: Documentation 🔄
- [ ] Create usage guide for the template
- [ ] Add examples of filled-in templates
- [ ] Document best practices for AI-assisted development

**Timeline**: Initial release ready (Phase 1-2 complete)

**Success criteria**:
- Template can be cloned and customized in <30 minutes
- AI agents can understand project context from CLAUDE.md
- Human developers find README.md welcoming and informative
- ADRs provide clear decision history

---

## Risks and Mitigation

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| Template too complex for small projects | Medium | Medium | Provide guidance on which parts to keep/remove |
| Documentation drifts out of sync | High | High | Add sync reminders in template instructions |
| Users don't customize placeholders | Medium | High | Add prominent customization checklists |
| Over-optimization for Claude vs other AI | Low | Low | AGENTS.md ensures universal compatibility |

---

## References

**Documentation Standards**:
- [Architecture Decision Records](https://adr.github.io/)
- [Keep a Changelog](https://keepachangelog.com/)
- [Conventional Commits](https://www.conventionalcommits.org/)

**AI Agent Documentation**:
- Claude Code documentation
- GitHub Copilot best practices
- Cursor AI documentation

**Related Decisions**:
- This is ADR #001, the foundational decision

---

## Notes

### Why this matters for AI-assisted development:

1. **Context is everything** - AI agents are only as good as the context they receive
2. **Discoverability** - AI needs clear pointers to find relevant information
3. **Decision history** - ADRs help AI understand *why*, not just *what*
4. **Consistency** - Standardized structure helps AI learn project patterns faster

### Future enhancements to consider:

- Tool to validate template customization
- GitHub Action to check doc sync
- Examples of filled templates for different project types
- Integration guides for specific AI tools

### Lessons learned:

- Balance is key - need both human and AI optimization
- Cross-references are critical - hub-and-spoke from CLAUDE.md works well
- Templates need clear instructions - customization checklists essential
- Bilingual support appreciated - Korean explanations help broader audience

---

## For AI Agents

**Impact on codebase**:
- This ADR defines the documentation structure all AI agents should reference
- CLAUDE.md is your primary entry point - read it first
- Follow cross-references from CLAUDE.md to find specific information
- Check meta/decisions/ for architectural context

**Patterns to follow**:
- When asked about the project, start with CLAUDE.md
- Reference ADRs when explaining architectural decisions
- Update CLAUDE.md when making significant changes
- Create new ADRs for major architectural decisions

**What to avoid**:
- Don't assume structure - check CLAUDE.md for current organization
- Don't skip ADRs - they contain critical context
- Don't create documentation outside this structure without good reason

---

_This ADR establishes the foundation for AI-optimized project documentation._
