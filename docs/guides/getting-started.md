# Getting Started

<!-- TEMPLATE INSTRUCTIONS / 템플릿 작성 가이드
이 문서는 프로젝트의 첫 사용자를 위한 가이드입니다.
This document is the first-time user guide for your project.

핵심 원칙 / Core Principles:
1. 순차적 진행: 사용자가 위에서 아래로 따라하면 성공하도록 작성
   Sequential Flow: Users should succeed by following top-to-bottom

2. 검증 가능: 각 단계마다 성공 여부를 확인할 수 있어야 함
   Verifiable: Each step should have verification checkpoints

3. 명확한 출력: 예상되는 출력을 보여주어 사용자가 확인할 수 있도록
   Clear Output: Show expected output so users can verify

4. AI 친화적: 에이전트가 단계를 자동화할 수 있도록 명확한 명령어 사용
   AI-Friendly: Use clear commands that agents can automate

작성 팁 / Writing Tips:
- Prerequisites: 버전 번호, 필수 도구, 권한 등 명확히 명시
  Prerequisites: Clearly specify version numbers, required tools, permissions

- Commands: 실제 실행 가능한 명령어만 작성 (플레이스홀더 최소화)
  Commands: Write actual executable commands (minimize placeholders)

- Verification: 각 주요 단계 후 확인 방법 제공
  Verification: Provide verification steps after each major step

- Next Steps: 다음에 볼 문서를 명확히 안내
  Next Steps: Clearly guide to the next documents to read
-->

> First-time setup guide for {{project-name}}.
>
> **Navigation**: [docs/](../index.md) > guides > getting-started

---

## Prerequisites

<!-- 필수 요구사항 / Required dependencies -->
<!-- ✅ DO: Specify exact or minimum versions -->
<!-- ❌ DON'T: Use vague requirements like "latest" -->

- Node.js >= 18.0.0
- npm >= 9.0.0
- Git 2.0+
- _[Add system requirements, e.g., OS, memory, disk space]_
- _[Add accounts/credentials needed, e.g., API keys, database access]_
- _[Add optional tools that enhance experience]_

<!-- 예시 / Example:
- Docker >= 20.10 (for containerized development)
- PostgreSQL 14+ (or use Docker Compose)
- GitHub account (for OAuth integration)
-->

---

## Installation

<!-- 설치 단계 / Installation steps -->
<!-- 각 단계는 독립적으로 실행 가능해야 함 / Each step should be independently executable -->

### 1. Clone the Repository

```bash
# Replace [owner] with your GitHub username/organization
# Replace {{project-name}} with your repository name
git clone https://github.com/[owner]/{{project-name}}.git
cd {{project-name}}
```

**Verify**: You should see the project files:
```bash
ls -la
# Expected: README.md, package.json, src/, docs/, etc.
```

### 2. Install Dependencies

```bash
npm install
# or: yarn install
# or: pnpm install
```

**Verify**: Check for `node_modules/`:
```bash
ls node_modules/ | head -5
# Expected: List of package directories
```

### 3. Configure Environment

```bash
# Copy the example environment file
cp .env.example .env

# Edit with your preferred editor
# vim .env
# nano .env
# code .env
```

**Required variables** (see [Configuration Guide](./configuration.md) for details):
```bash
# .env example / .env 예시
NODE_ENV=development
DATABASE_URL=postgresql://user:password@localhost:5432/dbname
API_KEY=your_api_key_here
# [Add project-specific required variables]
```

**Verify**: Environment file exists and contains required variables:
```bash
cat .env | grep -E "NODE_ENV|DATABASE_URL|API_KEY"
# Expected: Variables should be set (not empty)
```

### 4. Initialize Database (if applicable)

<!-- 데이터베이스가 필요한 경우 / If your project uses a database -->
```bash
# Run migrations
npm run db:migrate

# Seed initial data (optional)
npm run db:seed
```

**Verify**: Check database connection:
```bash
npm run db:status
# Expected: "Database connected" or similar success message
```

### 5. Run the Application

```bash
# Development mode with hot reload
npm run dev

# Or production build
# npm run build && npm start
```

**Verify**: Application is running:
- Open browser: http://localhost:3000 (or your configured port)
- Expected: Welcome page or main interface loads
- Check logs: Should see "Server running on port 3000" or similar

---

## Verify Installation

<!-- 전체 설치 검증 / Complete installation verification -->
Run the test suite to ensure everything is set up correctly:

```bash
npm test
```

**Expected output**:
```
✓ All tests passed (X tests)
Time: Xs
```

**If tests fail**:
1. Check [Troubleshooting Guide](./troubleshooting.md)
2. Verify all prerequisites are installed
3. Ensure environment variables are set correctly

---

## Quick Start Example

<!-- 빠른 시작 예제 / Quick example to verify functionality -->
Try a basic operation to confirm the installation works:

```bash
# [Replace with your project's hello-world command]
npm run example:basic

# Or use the CLI
npx {{project-name}} --help
```

**Expected**: Command completes successfully and shows output.

---

## Next Steps

<!-- 다음 단계 안내 / Guide to next steps -->
Now that you're set up, explore these resources:

1. **Configuration**: [Configuration Guide](./configuration.md) - Customize settings for your environment
2. **Usage**: [Basic Usage Examples](../examples/basic-usage.md) - Learn common patterns and workflows
3. **API**: [API Reference](../api/reference.md) - Explore available APIs and endpoints
4. **Architecture**: [Architecture Overview](../architecture/overview.md) - Understand how the system works

**Recommended learning path for new users**:
```
Getting Started (you are here)
    ↓
Configuration → Basic Usage → Advanced Usage
    ↓              ↓
Troubleshooting   API Reference
```

---

## Development Setup (Optional)

<!-- 개발자용 추가 설정 / Additional setup for contributors -->
If you plan to contribute or develop:

```bash
# Install development dependencies
npm install --include=dev

# Set up pre-commit hooks
npm run prepare

# Run linter
npm run lint

# Run type checker
npm run typecheck
```

See [Contributing Guide](../../meta/contributing.md) for more details.

---

## Troubleshooting

Having issues? Common solutions:

| Issue | Quick Fix |
|-------|-----------|
| `npm install` fails | Clear cache: `npm cache clean --force && rm -rf node_modules && npm install` |
| Port already in use | Change port in `.env`: `PORT=3001` |
| Database connection error | Verify `DATABASE_URL` in `.env` and database is running |

For detailed troubleshooting, see [Troubleshooting Guide](./troubleshooting.md).

---

## Related Documents

- [Configuration](./configuration.md) - Environment and application settings
- [Troubleshooting](./troubleshooting.md) - Common issues and solutions
- [Project Context](../../CLAUDE.md) - Project overview for AI agents
- [Contributing](../../meta/contributing.md) - How to contribute to this project

---

<!-- WRITING CHECKLIST / 작성 체크리스트
Before publishing this guide, verify:
이 가이드를 게시하기 전에 확인하세요:

□ All prerequisites have specific version numbers
  모든 필수 요구사항에 구체적인 버전 번호 명시

□ Every command is tested and works in sequence
  모든 명령어가 순서대로 테스트되고 작동함

□ Verification steps are provided after major steps
  주요 단계 후 검증 단계 제공

□ Expected outputs are shown for key commands
  주요 명령어의 예상 출력 표시

□ Next steps are clearly linked and prioritized
  다음 단계가 명확히 링크되고 우선순위 지정

□ Troubleshooting link is provided
  문제 해결 링크 제공

□ A fresh user can complete this guide in under 15 minutes
  새로운 사용자가 15분 내에 이 가이드를 완료할 수 있음
-->
