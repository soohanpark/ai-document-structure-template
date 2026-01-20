# Changelog

> **TEMPLATE INSTRUCTIONS**
>
> This changelog follows the [Keep a Changelog](https://keepachangelog.com/) format.
> When using this template:
> 1. Replace `{{project-name}}` with your project name
> 2. Replace `{{owner}}` and `{{repo}}` with GitHub owner/repo names
> 3. Update version numbers and dates as you release
> 4. Keep entries under [Unreleased] until you create a release
> 5. Move [Unreleased] items to a new version section when releasing
> 6. Update comparison links at the bottom
>
> **이 파일은 변경 이력 템플릿입니다**
> - 버전별로 변경사항을 기록하세요
> - Keep a Changelog 형식을 따릅니다
> - 릴리즈 시 [Unreleased] 항목을 버전 섹션으로 이동하세요

---

# Changelog for {{project-name}}

> All notable changes to this project will be documented in this file.
>
> The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
> and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added
- _[New features, endpoints, components, etc.]_

### Changed
- _[Changes to existing features]_

### Deprecated
- _[Features to be removed in future versions]_

### Removed
- _[Removed features]_

### Fixed
- _[Bug fixes]_

### Security
- _[Security updates and patches]_

---

## [1.0.0] - YYYY-MM-DD

### Added
- Initial release
- AI-optimized documentation structure
- CLAUDE.md as primary AI context
- AGENTS.md for universal AI agent support
- Comprehensive documentation hierarchy (docs/, meta/)
- Architecture Decision Records (ADR) framework
- Template-based project setup

---

## Version Numbering Guide

This project uses [Semantic Versioning](https://semver.org/):

**Format**: `MAJOR.MINOR.PATCH`

- **MAJOR** (1.0.0): Breaking changes, incompatible API changes
- **MINOR** (0.1.0): New features, backwards compatible
- **PATCH** (0.0.1): Bug fixes, backwards compatible

### Examples:

| Version | Type | Example Change |
|---------|------|----------------|
| 1.0.0 → 2.0.0 | MAJOR | Removed deprecated API, changed data structure |
| 1.0.0 → 1.1.0 | MINOR | Added new feature, new API endpoint |
| 1.0.0 → 1.0.1 | PATCH | Fixed bug, security patch |

### Pre-release versions:

- `1.0.0-alpha.1` - Alpha release (unstable)
- `1.0.0-beta.1` - Beta release (feature complete, needs testing)
- `1.0.0-rc.1` - Release candidate (stable, final testing)

---

## Release Notes Template

When creating a new release, use this template:

```markdown
## [X.Y.Z] - YYYY-MM-DD

### Added
- New feature: [Description]
- New API endpoint: `POST /api/resource`

### Changed
- Improved performance of [feature]
- Updated dependency X from v1.0 to v2.0

### Deprecated
- `oldFunction()` will be removed in v2.0.0
  - Use `newFunction()` instead
  - Migration guide: [link]

### Removed
- Removed deprecated `feature` (deprecated since v1.5.0)

### Fixed
- Fixed bug where [description] (#issue-number)
- Corrected typo in documentation

### Security
- Patched vulnerability CVE-YYYY-XXXXX
- Updated dependency to address security issue
```

---

## Changelog Best Practices

### Categories Explained:

- **Added**: New features, files, endpoints, capabilities
- **Changed**: Changes to existing functionality
- **Deprecated**: Features that will be removed soon
- **Removed**: Features that have been removed
- **Fixed**: Bug fixes
- **Security**: Security fixes and updates

### Writing Good Changelog Entries:

1. **Be specific**: "Fixed login bug" → "Fixed bug where login failed with special characters in password"
2. **Reference issues**: Include issue/PR numbers when relevant
3. **User-focused**: Write from the user's perspective
4. **Group related changes**: Keep related changes together
5. **Link to docs**: Link to migration guides for breaking changes

### Example Entries:

**Good**:
```markdown
### Added
- Added support for OAuth2 authentication (#123)
- New `--verbose` flag for detailed logging (#125)

### Fixed
- Fixed memory leak in database connection pool (#130)
- Corrected API response format for `/users` endpoint (#132)
```

**Bad**:
```markdown
### Added
- Stuff

### Fixed
- Bug fixes
```

---

## For AI Agents

When updating this changelog:

1. **Always update [Unreleased]** when making changes
2. **Use specific, clear descriptions** so AI can understand change context
3. **Include issue/PR numbers** for traceability
4. **Move unreleased items** to version sections when creating releases
5. **Update comparison links** at the bottom when releasing

This helps maintain accurate project history that both humans and AI can understand.

---

## Links

<!-- Update these links when creating releases -->
- [Unreleased]: https://github.com/{{owner}}/{{repo}}/compare/v1.0.0...HEAD
- [1.0.0]: https://github.com/{{owner}}/{{repo}}/releases/tag/v1.0.0

---

## Customization Checklist

**Before using this template**:

- [ ] Replace `{{project-name}}` with your project name
- [ ] Replace `{{owner}}/{{repo}}` with your GitHub repository
- [ ] Update the [1.0.0] section with your actual initial release details
- [ ] Set the release date in [1.0.0] section
- [ ] Update comparison links at the bottom
- [ ] Remove this checklist
- [ ] Start adding your changes to [Unreleased]

---

_Last updated: {{date}}_
