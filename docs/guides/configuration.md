# Configuration Guide

<!-- TEMPLATE INSTRUCTIONS / 템플릿 작성 가이드
이 문서는 프로젝트의 설정 옵션을 설명합니다.
This document explains the configuration options for your project.

핵심 원칙 / Core Principles:
1. 계층적 구조: 설정 파일 → 환경 변수 → 옵션으로 구조화
   Hierarchical: Structure as config files → env vars → options

2. 완전성: 모든 설정 옵션을 문서화
   Completeness: Document ALL configuration options

3. 예제 중심: 실제 사용 가능한 예제 제공
   Example-Driven: Provide real, usable examples

4. 우선순위 명확화: 설정 충돌 시 어떤 것이 우선하는지 명시
   Priority Clarity: Specify which config takes precedence

작성 팁 / Writing Tips:
- 각 변수에 타입, 기본값, 필수 여부 명시
  Specify type, default value, required status for each variable

- 민감한 정보(API 키 등)는 절대 실제 값을 예제로 사용하지 말 것
  Never use real secrets in examples

- 개발/스테이징/프로덕션 환경별 설정 차이 설명
  Explain differences between dev/staging/production configs

- AI 에이전트가 자동으로 설정 파일을 생성할 수 있도록 명확한 형식 제공
  Provide clear format so AI agents can auto-generate config files
-->

> Configuration options for {{project-name}}.
>
> **Navigation**: [docs/](../index.md) > guides > configuration

---

## Configuration Files

<!-- 설정 파일 개요 / Configuration files overview -->
<!-- 모든 설정 파일의 위치와 목적을 명시 / List all config files with locations and purposes -->

| File | Purpose | Format | Priority |
|------|---------|--------|----------|
| `.env` | Environment-specific variables (secrets, URLs) | Key-Value | 1 (Highest) |
| `config.json` | Application configuration (features, limits) | JSON | 2 |
| `tsconfig.json` | TypeScript compiler settings | JSON | - |
| `package.json` | Project metadata and scripts | JSON | - |
| _[config.yaml]_ | _[Optional: YAML config if used]_ | YAML | _[3]_ |

**Configuration priority** (highest to lowest):
1. Environment variables (`.env`, system env)
2. Configuration files (`config.json`, `config.yaml`)
3. Command-line arguments
4. Default values (hardcoded in application)

---

## Environment Variables

<!-- 환경 변수 / Environment variables -->
<!-- 모든 환경 변수를 표로 정리 / Document all environment variables in a table -->

### Core Variables

| Variable | Type | Description | Default | Required | Example |
|----------|------|-------------|---------|----------|---------|
| `NODE_ENV` | `string` | Runtime environment (`development`\|`production`\|`test`) | `development` | No | `production` |
| `PORT` | `number` | Server port | `3000` | No | `8080` |
| `LOG_LEVEL` | `string` | Logging verbosity (`debug`\|`info`\|`warn`\|`error`) | `info` | No | `debug` |
| _[DATABASE_URL]_ | `string` | Database connection string | - | Yes | `postgresql://user:pass@localhost:5432/db` |
| _[API_KEY]_ | `string` | External API key | - | Yes | `sk_live_abc123...` |
| _[REDIS_URL]_ | `string` | Redis connection string | `redis://localhost:6379` | No | `redis://cache:6379` |

<!-- 추가 변수 예시 / Additional variable examples:
| JWT_SECRET | string | Secret key for JWT signing | - | Yes | `your-256-bit-secret` |
| MAX_UPLOAD_SIZE | number | Max file upload size in MB | 10 | No | 50 |
| ENABLE_FEATURE_X | boolean | Enable experimental feature X | false | No | true |
-->

### Security Variables

<!-- 보안 관련 변수는 별도 섹션으로 분리 / Separate security-related variables -->

| Variable | Type | Description | Default | Required | Example |
|----------|------|-------------|---------|----------|---------|
| _[SESSION_SECRET]_ | `string` | Secret for session encryption | - | Yes (prod) | `random-secret-string` |
| _[ALLOWED_ORIGINS]_ | `string` | CORS allowed origins (comma-separated) | `*` | No | `https://app.example.com,https://admin.example.com` |

### Example `.env` File

<!-- 실제 사용 가능한 .env 예제 / Real, usable .env example -->
```bash
# Environment / 실행 환경
NODE_ENV=development

# Server / 서버 설정
PORT=3000
LOG_LEVEL=debug

# Database / 데이터베이스
DATABASE_URL=postgresql://user:password@localhost:5432/{{project-name}}_dev
# For production: postgresql://user:password@db-host:5432/{{project-name}}_prod

# External Services / 외부 서비스
API_KEY=your_api_key_here
REDIS_URL=redis://localhost:6379

# Security / 보안 (Generate with: openssl rand -base64 32)
SESSION_SECRET=your-session-secret-here
ALLOWED_ORIGINS=http://localhost:3000

# Feature Flags / 기능 플래그 (Optional)
# ENABLE_FEATURE_X=true
# MAX_UPLOAD_SIZE=10
```

**Security Notes**:
- Never commit `.env` to version control
- Use `.env.example` as a template (no real secrets)
- Rotate secrets regularly in production
- Use environment-specific `.env.development`, `.env.production` if needed

---

## Application Configuration

<!-- 애플리케이션 설정 파일 / Application config file -->
<!-- JSON/YAML 구조화된 설정 / Structured JSON/YAML config -->

### config.json

<!-- 전체 설정 구조 예제 / Complete config structure example -->
```json
{
  "app": {
    "name": "{{project-name}}",
    "version": "1.0.0",
    "environment": "development"
  },
  "server": {
    "port": 3000,
    "hostname": "localhost",
    "timeout": 30000
  },
  "database": {
    "poolSize": 10,
    "connectionTimeout": 5000,
    "ssl": false
  },
  "features": {
    "enableCaching": true,
    "enableRateLimiting": true,
    "maxRequestsPerMinute": 60
  },
  "logging": {
    "level": "info",
    "format": "json",
    "outputFile": "logs/app.log"
  }
}
```

### Configuration Options Reference

<!-- 각 설정 옵션의 상세 설명 / Detailed explanation of each option -->

#### App Settings

| Option | Type | Description | Default | Valid Values |
|--------|------|-------------|---------|--------------|
| `app.name` | `string` | Application name | `"{{project-name}}"` | Any string |
| `app.version` | `string` | Application version | `"1.0.0"` | Semantic version |
| `app.environment` | `string` | Runtime environment | `"development"` | `development`, `staging`, `production` |

#### Server Settings

| Option | Type | Description | Default | Valid Values |
|--------|------|-------------|---------|--------------|
| `server.port` | `number` | HTTP port to listen on | `3000` | 1-65535 |
| `server.hostname` | `string` | Host to bind to | `"localhost"` | Any valid hostname/IP |
| `server.timeout` | `number` | Request timeout (ms) | `30000` | > 0 |

#### Database Settings

| Option | Type | Description | Default | Valid Values |
|--------|------|-------------|---------|--------------|
| `database.poolSize` | `number` | Max connection pool size | `10` | 1-100 |
| `database.connectionTimeout` | `number` | Connection timeout (ms) | `5000` | > 0 |
| `database.ssl` | `boolean` | Use SSL for connections | `false` | `true`, `false` |

#### Feature Flags

| Option | Type | Description | Default | Valid Values |
|--------|------|-------------|---------|--------------|
| `features.enableCaching` | `boolean` | Enable response caching | `true` | `true`, `false` |
| `features.enableRateLimiting` | `boolean` | Enable rate limiting | `true` | `true`, `false` |
| `features.maxRequestsPerMinute` | `number` | Rate limit threshold | `60` | > 0 |

#### Logging Settings

| Option | Type | Description | Default | Valid Values |
|--------|------|-------------|---------|--------------|
| `logging.level` | `string` | Log level | `"info"` | `debug`, `info`, `warn`, `error` |
| `logging.format` | `string` | Log format | `"json"` | `json`, `text`, `pretty` |
| `logging.outputFile` | `string` | Log file path | `"logs/app.log"` | Any valid path |

---

## Environment-Specific Configuration

<!-- 환경별 설정 차이 / Environment-specific differences -->

### Development

```bash
# .env.development
NODE_ENV=development
LOG_LEVEL=debug
DATABASE_URL=postgresql://localhost:5432/{{project-name}}_dev
ENABLE_HOT_RELOAD=true
```

**Recommended settings**:
- Verbose logging (`debug` level)
- Detailed error messages
- Disabled caching for real-time updates
- Permissive CORS for local testing

### Staging

```bash
# .env.staging
NODE_ENV=staging
LOG_LEVEL=info
DATABASE_URL=postgresql://staging-db:5432/{{project-name}}_staging
ENABLE_MONITORING=true
```

**Recommended settings**:
- Production-like environment
- Moderate logging
- Enable monitoring/metrics
- Test production configurations

### Production

```bash
# .env.production
NODE_ENV=production
LOG_LEVEL=warn
DATABASE_URL=postgresql://prod-db:5432/{{project-name}}
ENABLE_MONITORING=true
ENABLE_RATE_LIMITING=true
```

**Recommended settings**:
- Minimal logging (only warnings/errors)
- Strict security (rate limiting, CORS)
- Connection pooling enabled
- Health checks enabled

---

## Configuration Priority

<!-- 설정 우선순위 명확화 / Clarify configuration precedence -->

When the same setting is defined in multiple places, this order determines which value is used:

1. **Environment variables** (highest priority)
   - System environment variables
   - `.env` file variables

2. **Command-line arguments**
   - `node app.js --port=8080`

3. **Configuration files**
   - `config.json`
   - `config.yaml`

4. **Default values** (lowest priority)
   - Hardcoded in application code

### Example Priority Resolution

```bash
# .env file
PORT=3000

# config.json
{
  "server": {
    "port": 4000
  }
}

# Command: node app.js --port=5000

# Result: Server starts on port 5000 (command-line > env > config)
```

---

## Validation

<!-- 설정 검증 / Configuration validation -->

Validate your configuration before starting:

```bash
# Check configuration syntax
npm run config:validate

# Show merged configuration (all sources combined)
npm run config:show

# Test database connection
npm run config:test-db
```

**Expected output**:
```
✓ Configuration valid
✓ Database connection successful
✓ All required variables set
```

---

## Common Configuration Patterns

<!-- 일반적인 설정 패턴 / Common config patterns -->

### Using Docker

```bash
# docker-compose.yml environment section
environment:
  NODE_ENV: production
  DATABASE_URL: postgresql://db:5432/{{project-name}}
  REDIS_URL: redis://redis:6379
```

### Using Kubernetes

```yaml
# k8s-configmap.yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: {{project-name}}-config
data:
  NODE_ENV: "production"
  PORT: "3000"
```

### Using CI/CD

```yaml
# .github/workflows/deploy.yml
env:
  NODE_ENV: production
  DATABASE_URL: ${{ secrets.DATABASE_URL }}
  API_KEY: ${{ secrets.API_KEY }}
```

---

## Troubleshooting

<!-- 설정 관련 문제 해결 / Configuration troubleshooting -->

| Issue | Cause | Solution |
|-------|-------|----------|
| "Missing required variable" error | Required env var not set | Check `.env` file exists and contains all required variables |
| Settings not taking effect | Wrong configuration priority | Check order: env vars override config files |
| Database connection fails | Invalid `DATABASE_URL` | Verify connection string format and credentials |
| JSON parse error | Invalid JSON in `config.json` | Validate JSON syntax (use `jsonlint` or online validator) |

For more issues, see [Troubleshooting Guide](./troubleshooting.md).

---

## Related Documents

- [Getting Started](./getting-started.md) - Initial setup and installation
- [Troubleshooting](./troubleshooting.md) - Common issues and solutions
- [API Reference](../api/reference.md) - API configuration options
- [Architecture Overview](../architecture/overview.md) - System architecture and design

---

<!-- WRITING CHECKLIST / 작성 체크리스트
Before publishing this guide, verify:
이 가이드를 게시하기 전에 확인하세요:

□ All environment variables are documented with type and default
  모든 환경 변수가 타입과 기본값과 함께 문서화됨

□ Example config files are valid and tested
  예제 설정 파일이 유효하고 테스트됨

□ Security-sensitive variables are marked and explained
  보안에 민감한 변수가 표시되고 설명됨

□ Configuration priority is clearly explained
  설정 우선순위가 명확히 설명됨

□ Environment-specific differences are documented
  환경별 차이가 문서화됨

□ Validation commands are provided
  검증 명령어가 제공됨

□ No real secrets are exposed in examples
  예제에 실제 비밀 정보가 노출되지 않음
-->
