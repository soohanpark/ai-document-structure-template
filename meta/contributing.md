# Contributing Guide

> **TEMPLATE INSTRUCTIONS**
>
> This is a template for contribution guidelines. Customize for your project:
> 1. Replace `{{project-name}}` with your project name
> 2. Update development workflow steps based on your tech stack
> 3. Modify testing commands to match your setup
> 4. Adjust code review requirements as needed
> 5. Update issue template links if you create GitHub issue templates
> 6. Keep the ADR section - it encourages good documentation practices
>
> **이 파일은 기여 가이드 템플릿입니다**
> - 프로젝트별 개발 워크플로우를 정의하세요
> - 테스트/빌드 명령어를 업데이트하세요
> - 코드 리뷰 규칙을 명시하세요

---

# Contributing to {{project-name}}

> How to contribute to {{project-name}}.
>
> **Project Context**: [CLAUDE.md](../CLAUDE.md)

---

## Getting Started

1. Fork the repository
2. Clone your fork
3. Set up development environment (see [Getting Started](../docs/guides/getting-started.md))

---

## Development Workflow

### 1. Create a Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/issue-description
```

**Branch naming conventions**:
- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation changes
- `refactor/` - Code refactoring
- `test/` - Test additions/changes

### 2. Make Changes

- Follow [code conventions](../CLAUDE.md#code-conventions)
- Write tests for new features
- Update documentation if needed
- Keep changes focused and atomic

**For AI-assisted development**:
- Document significant decisions in commit messages
- Add inline comments for complex logic
- Update CLAUDE.md if you change architecture
- Consider creating an ADR for major architectural changes

### 3. Test Your Changes

```bash
# CUSTOMIZE THESE COMMANDS FOR YOUR PROJECT
npm test              # Run tests
npm run lint          # Check code style
npm run typecheck     # TypeScript type checking
npm run build         # Verify build succeeds
```

**Testing checklist**:
- [ ] All tests pass
- [ ] New features have tests
- [ ] Edge cases are covered
- [ ] No linting errors
- [ ] Build succeeds

### 4. Commit

```bash
git add .
git commit -m "feat: add new feature"
```

#### Commit Message Format

We use [Conventional Commits](https://www.conventionalcommits.org/):

```
type(scope): description

[optional body]

[optional footer]
```

**Types**:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting)
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance tasks
- `perf`: Performance improvements
- `ci`: CI/CD changes

**Examples**:
```
feat(auth): add OAuth2 authentication
fix(api): handle null response in getUserData
docs(readme): update installation instructions
refactor(core): extract validation logic
```

### 5. Push and Create PR

```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub.

**PR Guidelines**:
- Use a clear, descriptive title
- Reference related issues (e.g., "Fixes #123")
- Describe what changed and why
- Include screenshots for UI changes
- Check that CI passes
- Request reviews from relevant maintainers

---

## Code Review Process

1. **All PRs require at least one review**
2. **CI checks must pass** (tests, linting, build)
3. **Documentation must be updated** for new features
4. **Tests must be included** for new functionality
5. **Address review feedback** promptly

**For Reviewers**:
- Be constructive and respectful
- Focus on code quality, not style preferences
- Suggest improvements, don't just criticize
- Approve when satisfied, or request changes with clear guidance

---

## Working with AI Agents

This project is optimized for AI-assisted development:

### When using Claude Code or similar AI tools:

1. **Start with CLAUDE.md** - Primary context source
2. **Check AGENTS.md** - For AI-specific patterns
3. **Read relevant ADRs** - Understand past decisions
4. **Update documentation** - Keep AI context fresh

### AI-friendly contribution patterns:

- **Clear commit messages** - AI can understand project history
- **Inline documentation** - Helps AI understand intent
- **ADRs for big changes** - AI can reference decision context
- **Updated CLAUDE.md** - Keeps AI context accurate

---

## Reporting Issues

### Bug Reports

**Include**:
- Environment details (OS, Node.js version, npm/yarn version)
- Steps to reproduce
- Expected vs actual behavior
- Error messages and stack traces
- Screenshots (if UI-related)

**Template**:
```markdown
**Environment**:
- OS: [e.g., macOS 13.0]
- Node.js: [e.g., v18.17.0]
- {{project-name}} version: [e.g., 1.2.3]

**Steps to reproduce**:
1. ...
2. ...

**Expected behavior**: ...

**Actual behavior**: ...

**Error messages**:
\```
[paste error here]
\```
```

### Feature Requests

**Include**:
- Use case description (what problem does this solve?)
- Proposed solution (if any)
- Alternatives considered
- Additional context

**Template**:
```markdown
**Problem**: [What problem are you trying to solve?]

**Proposed solution**: [How would you like to solve it?]

**Alternatives**: [What other approaches did you consider?]

**Additional context**: [Any other relevant information]
```

---

## Documentation Contributions

Documentation lives in:
- `docs/` - Main documentation
- `meta/` - Project metadata and governance
- `CLAUDE.md` - Source of truth (update carefully)
- `AGENTS.md` - AI agent entry point

See [Documentation Structure](../CLAUDE.md#project-structure).

**Documentation guidelines**:
- Write clearly and concisely
- Include code examples
- Add Korean translations for key documents (optional)
- Update cross-references when moving files
- Keep CLAUDE.md synchronized with major changes

---

## Architecture Decisions

For significant changes, create an ADR (Architecture Decision Record):

**When to create an ADR**:
- Changing core architecture
- Adopting new major dependencies
- Modifying data structures
- Changing API contracts
- Making trade-offs between alternatives

**How to create an ADR**:

1. Copy [meta/decisions/template.md](./decisions/template.md)
2. Name it `NNN-title-in-kebab-case.md` (next sequential number)
3. Fill in the template:
   - **Context**: Why is this decision needed?
   - **Decision**: What are we doing?
   - **Consequences**: What are the implications?
   - **Alternatives**: What else did we consider?
4. Include in your PR
5. Update CLAUDE.md to reference the ADR if it affects AI context

**Example**: `002-switch-to-postgresql.md`

---

## Customization Checklist

**Before using this template**:

- [ ] Replace `{{project-name}}` with your project name
- [ ] Update test commands in section 3
- [ ] Adjust code review requirements
- [ ] Update branch naming conventions if needed
- [ ] Add GitHub issue template links
- [ ] Customize commit message types if needed
- [ ] Update environment details in bug report template
- [ ] Add project-specific contribution guidelines
- [ ] Remove this checklist

---

## Questions?

- Check existing [documentation](../docs/)
- Search [GitHub Issues](https://github.com/{{owner}}/{{project-name}}/issues)
- Create a new issue for discussion
- Ask in discussions (if enabled)

---

_Last updated: {{date}}_
