# Troubleshooting Guide

<!-- TEMPLATE INSTRUCTIONS / 템플릿 작성 가이드
이 문서는 일반적인 문제와 해결책을 제공합니다.
This document provides common issues and their solutions.

핵심 원칙 / Core Principles:
1. 증상 기반: 사용자가 보는 증상으로 시작
   Symptom-Based: Start with what users see

2. 진단 도구: 문제 파악을 위한 명령어 제공
   Diagnostic Tools: Provide commands to identify issues

3. 단계별 해결: 간단한 것부터 복잡한 것까지 순차적으로
   Step-by-Step: From simple to complex solutions

4. 검증 가능: 해결 후 확인 방법 제공
   Verifiable: Provide verification after fixes

작성 팁 / Writing Tips:
- 실제 에러 메시지를 예제로 사용
  Use actual error messages as examples

- 각 해결책에 설명과 명령어 모두 포함
  Include both explanation and commands for each solution

- 최후의 수단(데이터 삭제 등)은 명확히 경고
  Clearly warn about destructive actions

- AI 에이전트가 자동으로 진단하고 수정할 수 있도록 명확한 패턴 사용
  Use clear patterns so AI agents can auto-diagnose and fix
-->

> Common issues and solutions for {{project-name}}.
>
> **Navigation**: [docs/](../index.md) > guides > troubleshooting

---

## Quick Diagnostics

<!-- 빠른 진단 도구 / Quick diagnostic tools -->
<!-- 모든 사용자가 먼저 실행해야 할 명령어들 / Commands everyone should run first -->

Run these commands to collect diagnostic information:

```bash
# System Information / 시스템 정보
node --version          # Expected: v18.0.0 or higher
npm --version           # Expected: 9.0.0 or higher
git --version           # Expected: 2.0 or higher

# Project Status / 프로젝트 상태
npm list --depth=0      # Check installed packages
npm outdated            # Check for outdated packages

# Environment Check / 환경 변수 확인
echo $NODE_ENV          # Should show: development, production, etc.
cat .env | grep -v '^#' | grep -v '^$'  # Show non-empty env vars (⚠️ hide before sharing)

# Build & Test Status / 빌드 및 테스트 상태
npm run typecheck       # Check TypeScript compilation
npm run lint            # Check code style
npm test                # Run test suite
```

**Copy-paste friendly diagnostic report**:
```bash
# Generate diagnostic report for issue reporting
echo "=== Diagnostic Report ===" > diagnostic.txt
echo "Node: $(node --version)" >> diagnostic.txt
echo "npm: $(npm --version)" >> diagnostic.txt
echo "OS: $(uname -s)" >> diagnostic.txt
echo "Project: $(npm list {{project-name}} 2>/dev/null | head -2)" >> diagnostic.txt
cat diagnostic.txt
```

---

## Common Issues

<!-- 일반적인 문제들 / Common problems -->
<!-- 각 문제는 증상 → 원인 → 해결책 순서로 작성 / Each issue: Symptom → Cause → Solution -->

### Installation Issues

#### Issue: `npm install` Fails

**Symptoms**:
```
npm ERR! code ERESOLVE
npm ERR! ERESOLVE unable to resolve dependency tree
```

**Cause**: Dependency conflicts or corrupted cache

**Solution**:
```bash
# Step 1: Clear npm cache
npm cache clean --force

# Step 2: Remove existing node_modules
rm -rf node_modules package-lock.json

# Step 3: Reinstall with legacy peer deps (if needed)
npm install --legacy-peer-deps

# Verify: Check installation
npm list --depth=0
```

**Verification**: Should see "{{project-name}}@x.x.x" without errors.

---

#### Issue: Permission Errors During Install

**Symptoms**:
```
npm ERR! code EACCES
npm ERR! syscall access
npm ERR! path /usr/local/lib/node_modules
```

**Cause**: npm trying to write to system directories

**Solution**:
```bash
# Option 1: Fix npm permissions (recommended)
mkdir -p ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# Option 2: Use npx (no global install needed)
npx {{project-name}} [command]

# ⚠️ Option 3: Use sudo (NOT recommended)
# sudo npm install -g {{project-name}}
```

**Verification**: `npm install` should succeed without sudo.

---

### Build & Compilation Issues

#### Issue: TypeScript Compilation Errors

**Symptoms**:
```
error TS2307: Cannot find module 'xyz' or its corresponding type declarations
```

**Cause**: Missing type definitions or incorrect tsconfig

**Solution**:
```bash
# Step 1: Install missing types
npm install --save-dev @types/node @types/[missing-module]

# Step 2: Check tsconfig.json
cat tsconfig.json | grep -A5 "compilerOptions"

# Step 3: Rebuild
npm run build

# If still failing, try clean build
rm -rf dist/ .tsbuildinfo
npm run build
```

**Verification**: `npm run build` completes without errors.

---

#### Issue: Build Succeeds but Runtime Errors

**Symptoms**:
```
Error: Cannot find module './dist/index.js'
```

**Cause**: Build output path mismatch

**Solution**:
```bash
# Check build output directory
ls -la dist/

# Verify package.json main field
cat package.json | grep '"main"'
# Should match: "main": "dist/index.js"

# Check tsconfig.json outDir
cat tsconfig.json | grep "outDir"
# Should match: "outDir": "dist"

# Rebuild
npm run clean && npm run build
```

**Verification**: `npm start` or `node dist/index.js` runs successfully.

---

### Runtime Issues

#### Issue: Database Connection Fails

**Symptoms**:
```
Error: connect ECONNREFUSED 127.0.0.1:5432
```

**Cause**: Database not running or incorrect connection string

**Diagnostic**:
```bash
# Check if database is running
pg_isready -h localhost -p 5432
# Or for MySQL: mysqladmin ping -h localhost

# Test connection string
echo $DATABASE_URL
# Should be: postgresql://user:password@host:port/database
```

**Solution**:
```bash
# Option 1: Start database (PostgreSQL example)
# macOS: brew services start postgresql
# Linux: sudo systemctl start postgresql
# Docker: docker-compose up -d postgres

# Option 2: Fix connection string in .env
DATABASE_URL=postgresql://user:password@localhost:5432/{{project-name}}_dev

# Option 3: Use Docker Compose (if available)
docker-compose up -d db

# Verify connection
npm run db:status
# Or: psql $DATABASE_URL -c "SELECT 1"
```

**Verification**: Database connection succeeds.

---

#### Issue: Port Already in Use

**Symptoms**:
```
Error: listen EADDRINUSE: address already in use :::3000
```

**Cause**: Another process is using the port

**Diagnostic**:
```bash
# Find process using port 3000 (macOS/Linux)
lsof -i :3000

# Or use netstat (cross-platform)
netstat -tuln | grep 3000
```

**Solution**:
```bash
# Option 1: Kill the process
lsof -ti:3000 | xargs kill -9

# Option 2: Change port in .env
echo "PORT=3001" >> .env

# Option 3: Use a different port temporarily
PORT=3001 npm run dev
```

**Verification**: Server starts without port conflict.

---

#### Issue: Environment Variables Not Loaded

**Symptoms**:
- Settings revert to defaults
- "Missing required variable" errors

**Cause**: `.env` file not loaded or wrong location

**Diagnostic**:
```bash
# Check if .env exists
ls -la .env

# Check if dotenv is installed
npm list dotenv

# Check where .env is loaded in code
grep -r "dotenv" src/
```

**Solution**:
```bash
# Ensure .env file exists
cp .env.example .env

# Verify dotenv is installed
npm install --save dotenv

# Load .env at entry point (should be in code)
# Add to src/index.ts:
# import 'dotenv/config';

# Verify variables are set
node -e "require('dotenv').config(); console.log(process.env.NODE_ENV)"
```

**Verification**: Environment variables are accessible in application.

---

### Testing Issues

#### Issue: Tests Fail in CI but Pass Locally

**Symptoms**:
```
Tests: 5 failed, 10 passed, 15 total
(Locally: All 15 passed)
```

**Cause**: Environment differences or missing setup

**Solution**:
```bash
# Step 1: Run tests with same environment as CI
NODE_ENV=test npm test

# Step 2: Check for missing test environment variables
cat .env.test
# Ensure CI has equivalent environment variables

# Step 3: Clear test cache
npm test -- --clearCache

# Step 4: Run tests in isolation
npm test -- --runInBand
```

**Verification**: Tests pass consistently in both environments.

---

## Issue Template

<!-- 새로운 문제를 추가할 때 사용할 템플릿 / Template for adding new issues -->

<!--
### Issue: _[Clear, Searchable Title]_

**Symptoms**:
- _[What the user sees - error message, behavior]_
- _[Include actual error text for searchability]_

**Cause**: _[Why this happens - root cause]_

**Diagnostic** (optional):
```bash
# Commands to identify the problem
[diagnostic-command]
```

**Solution**:
```bash
# Step-by-step fix
[fix-command-1]
[fix-command-2]
```

**Verification**: _[How to confirm it's fixed]_

---
-->

---

## Diagnostic Commands Reference

<!-- 진단 명령어 참고자료 / Diagnostic commands reference -->

| Problem Area | Diagnostic Command | What It Shows |
|--------------|-------------------|---------------|
| Node/npm version | `node -v && npm -v` | Installed versions |
| Package issues | `npm list --depth=0` | Installed packages |
| TypeScript | `npx tsc --noEmit` | Type errors without building |
| Environment | `printenv \| grep NODE` | Node-related env vars |
| Database | `npm run db:status` | Database connection status |
| Port usage | `lsof -i :3000` | Process using port 3000 |
| Disk space | `df -h .` | Available disk space |
| Memory | `free -h` (Linux) / `vm_stat` (macOS) | Memory usage |

---

## Getting Help

<!-- 도움 받기 / Getting help -->

If your issue isn't listed here or solutions don't work:

### Before Asking for Help

Collect this information:

```bash
# Run diagnostic script
npm run diagnose

# Or manually collect:
# 1. System info
node -v && npm -v && uname -a

# 2. Error message (full stack trace)
# Copy from terminal or logs

# 3. Steps to reproduce
# List exact commands that cause the issue

# 4. Expected vs actual behavior
# Describe what should happen and what actually happens
```

### Where to Get Help

1. **Search existing issues**: [GitHub Issues](https://github.com/[owner]/{{project-name}}/issues)
   - Use error message keywords
   - Check closed issues too

2. **Ask in community**:
   - [Discord/Slack channel]
   - [Stack Overflow tag: {{project-name}}]

3. **Create new issue**: [New Issue](https://github.com/[owner]/{{project-name}}/issues/new)

### Issue Report Template

When creating a new issue, include:

```markdown
## Environment
- Node version: [run: node -v]
- npm version: [run: npm -v]
- OS: [macOS/Linux/Windows + version]
- {{project-name}} version: [run: npm list {{project-name}}]

## Expected Behavior
[What should happen]

## Actual Behavior
[What actually happens]

## Steps to Reproduce
1. [First step]
2. [Second step]
3. [etc.]

## Error Message
```
[Paste full error message here]
```

## What I've Tried
- [Solution 1 from troubleshooting guide]
- [Solution 2 from troubleshooting guide]
```

---

## Emergency Recovery

<!-- 긴급 복구 / Emergency recovery -->

If nothing works and you need to start fresh:

```bash
# ⚠️ DESTRUCTIVE: This will delete all local changes
# Make sure you've committed any important work first!

# Step 1: Backup your .env and custom configs
cp .env .env.backup
cp config.json config.json.backup

# Step 2: Clean everything
rm -rf node_modules package-lock.json dist .tsbuildinfo
npm cache clean --force

# Step 3: Reset to clean state (if using git)
git clean -fdx  # ⚠️ Removes all untracked files
git reset --hard origin/main

# Step 4: Reinstall
npm install

# Step 5: Restore configs
cp .env.backup .env
cp config.json.backup config.json

# Step 6: Rebuild
npm run build

# Step 7: Verify
npm test
```

**Verification**: Application works as if freshly cloned.

---

## Prevention Tips

<!-- 문제 예방 팁 / Problem prevention tips -->

Avoid common issues by:

1. **Keep dependencies updated**:
   ```bash
   npm outdated
   npm update
   ```

2. **Run tests before committing**:
   ```bash
   npm test && git commit
   ```

3. **Use version control for configs**:
   - Commit `.env.example` (without secrets)
   - Never commit `.env` (with secrets)

4. **Regular health checks**:
   ```bash
   npm run lint && npm run typecheck && npm test
   ```

5. **Document custom setup**:
   - Add project-specific setup to this guide
   - Update when you fix a new issue

---

## Related Documents

- [Getting Started](./getting-started.md) - Installation and setup
- [Configuration](./configuration.md) - Configuration options and environment variables
- [Contributing](../../meta/contributing.md) - Development workflow and guidelines
- [Architecture](../architecture/overview.md) - System architecture (for advanced debugging)

---

<!-- WRITING CHECKLIST / 작성 체크리스트
Before publishing this guide, verify:
이 가이드를 게시하기 전에 확인하세요:

□ All common issues from user reports are documented
  사용자 보고서의 모든 일반적인 문제가 문서화됨

□ Each issue has clear symptoms with actual error messages
  각 문제에 실제 에러 메시지가 포함된 명확한 증상이 있음

□ Solutions are tested and verified to work
  해결책이 테스트되고 작동하는 것으로 확인됨

□ Diagnostic commands are provided before solutions
  해결책 전에 진단 명령어가 제공됨

□ Destructive operations are clearly marked with ⚠️
  파괴적인 작업이 ⚠️로 명확히 표시됨

□ Issue report template is complete and helpful
  이슈 리포트 템플릿이 완전하고 유용함

□ Emergency recovery steps are tested
  긴급 복구 단계가 테스트됨
-->
