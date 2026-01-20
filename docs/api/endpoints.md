# REST API Endpoints

> HTTP API endpoint specifications for {{project-name}}.
>
> **Navigation**: [docs/](../index.md) > api > endpoints

---

## Template Instructions

<!--
이 문서는 REST API 엔드포인트 전용입니다.
This document is specifically for REST API endpoints.

프로젝트에 HTTP API가 없는 경우:
If your project doesn't have an HTTP API:
- 이 파일을 삭제하거나
  Delete this file, or
- reference.md의 CLI Commands 또는 Functions API 섹션을 사용하세요
  Use the CLI Commands or Functions API sections in reference.md

REST API가 있는 경우:
If you have a REST API:
- 각 엔드포인트를 아래 템플릿에 따라 문서화하세요
  Document each endpoint following the templates below
- OpenAPI/Swagger 스펙도 고려하세요
  Consider also maintaining an OpenAPI/Swagger spec
-->

---

## Overview

**Base URL**:
```
# Development
http://localhost:3000/api

# Production
https://api.{{project-name}}.com
```

**API Version**: `v1`

**Content-Type**: `application/json`

**Authentication**: _[None / API Key / Bearer Token / etc.]_

---

## Authentication

<!--
인증이 필요한 경우 이 섹션을 작성하세요
Complete this section if your API requires authentication
-->

### API Key Authentication

**Header**:
```
X-API-Key: your-api-key-here
```

**Example**:
```bash
curl -H "X-API-Key: abc123..." https://api.{{project-name}}.com/endpoint
```

**How to get an API key**: _[API 키 발급 방법 설명]_

---

### Bearer Token Authentication

**Header**:
```
Authorization: Bearer your-token-here
```

**Example**:
```bash
curl -H "Authorization: Bearer eyJhbG..." https://api.{{project-name}}.com/endpoint
```

**Token Lifetime**: _[토큰 유효 기간]_

**Refresh Token**: _[토큰 갱신 방법]_

---

## Common Headers

| Header | Required | Description |
|--------|----------|-------------|
| `Content-Type` | For POST/PUT/PATCH | Must be `application/json` |
| `Accept` | No | Response format (default: `application/json`) |
| `X-API-Key` | If auth required | Your API key |
| `X-Request-ID` | No | Client-provided request ID for tracing |

---

## Endpoints

### Resource: Users
<!-- 리소스별로 그룹화하여 문서화 / Group by resource -->

#### `GET /users`

_[사용자 목록 조회]_
_[Retrieve a list of users]_

**Query Parameters**:
| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `page` | `integer` | No | `1` | _[페이지 번호 (1부터 시작)]_ |
| `limit` | `integer` | No | `10` | _[페이지당 항목 수 (최대 100)]_ |
| `sort` | `string` | No | `created_at` | _[정렬 기준: `created_at`, `name`, `email`]_ |
| `order` | `string` | No | `desc` | _[정렬 방향: `asc`, `desc`]_ |
| `search` | `string` | No | - | _[검색 키워드 (이름, 이메일)]_ |

**Request**:
```bash
# 기본 조회 / Basic query
curl http://localhost:3000/api/users

# 페이지네이션 / With pagination
curl "http://localhost:3000/api/users?page=2&limit=20"

# 검색 / With search
curl "http://localhost:3000/api/users?search=john&sort=name&order=asc"
```

**Response** `200 OK`:
```json
{
  "status": "success",
  "data": {
    "users": [
      {
        "id": "user_123",
        "name": "John Doe",
        "email": "john@example.com",
        "created_at": "2026-01-20T10:00:00Z",
        "updated_at": "2026-01-20T10:00:00Z"
      }
    ],
    "pagination": {
      "page": 1,
      "limit": 10,
      "total": 42,
      "total_pages": 5
    }
  }
}
```

**Status Codes**:
| Code | Description |
|------|-------------|
| 200 | Success |
| 400 | Invalid query parameters |
| 401 | Unauthorized (missing or invalid auth) |
| 429 | Rate limit exceeded |
| 500 | Internal server error |

---

#### `GET /users/:id`

_[특정 사용자 조회]_
_[Retrieve a specific user by ID]_

**Path Parameters**:
| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | `string` | _[사용자 ID]_ |

**Request**:
```bash
curl http://localhost:3000/api/users/user_123
```

**Response** `200 OK`:
```json
{
  "status": "success",
  "data": {
    "id": "user_123",
    "name": "John Doe",
    "email": "john@example.com",
    "profile": {
      "bio": "Software developer",
      "avatar_url": "https://..."
    },
    "created_at": "2026-01-20T10:00:00Z",
    "updated_at": "2026-01-20T10:00:00Z"
  }
}
```

**Status Codes**:
| Code | Description |
|------|-------------|
| 200 | Success |
| 404 | User not found |
| 401 | Unauthorized |

---

#### `POST /users`

_[새 사용자 생성]_
_[Create a new user]_

**Request Headers**:
```
Content-Type: application/json
X-API-Key: your-api-key
```

**Request Body**:
| Field | Type | Required | Validation | Description |
|-------|------|----------|------------|-------------|
| `name` | `string` | Yes | 1-100 chars | _[사용자 이름]_ |
| `email` | `string` | Yes | Valid email | _[이메일 주소]_ |
| `password` | `string` | Yes | Min 8 chars | _[비밀번호]_ |
| `profile` | `object` | No | - | _[프로필 정보]_ |
| `profile.bio` | `string` | No | Max 500 chars | _[자기소개]_ |

**Request**:
```bash
curl -X POST http://localhost:3000/api/users \
  -H "Content-Type: application/json" \
  -H "X-API-Key: your-api-key" \
  -d '{
    "name": "Jane Smith",
    "email": "jane@example.com",
    "password": "secure-password-123",
    "profile": {
      "bio": "Product designer"
    }
  }'
```

**Response** `201 Created`:
```json
{
  "status": "success",
  "data": {
    "id": "user_456",
    "name": "Jane Smith",
    "email": "jane@example.com",
    "profile": {
      "bio": "Product designer",
      "avatar_url": null
    },
    "created_at": "2026-01-20T12:00:00Z",
    "updated_at": "2026-01-20T12:00:00Z"
  }
}
```

**Status Codes**:
| Code | Description |
|------|-------------|
| 201 | User created successfully |
| 400 | Invalid request body |
| 409 | Email already exists |
| 422 | Validation error |

**Error Response Example** `422 Unprocessable Entity`:
```json
{
  "status": "error",
  "message": "Validation failed",
  "code": "VALIDATION_ERROR",
  "errors": [
    {
      "field": "email",
      "message": "Invalid email format"
    },
    {
      "field": "password",
      "message": "Password must be at least 8 characters"
    }
  ]
}
```

---

#### `PUT /users/:id`

_[사용자 정보 전체 업데이트 (전체 교체)]_
_[Full update (replace) a user]_

**Path Parameters**:
| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | `string` | _[사용자 ID]_ |

**Request Body**: _[Same as POST /users, all fields required]_

**Request**:
```bash
curl -X PUT http://localhost:3000/api/users/user_123 \
  -H "Content-Type: application/json" \
  -H "X-API-Key: your-api-key" \
  -d '{
    "name": "John Updated",
    "email": "john.new@example.com",
    "password": "new-password-456"
  }'
```

**Response** `200 OK`: _[Same structure as GET /users/:id]_

---

#### `PATCH /users/:id`

_[사용자 정보 부분 업데이트]_
_[Partial update a user]_

**Path Parameters**:
| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | `string` | _[사용자 ID]_ |

**Request Body** (all fields optional):
| Field | Type | Description |
|-------|------|-------------|
| `name` | `string` | _[새 이름]_ |
| `email` | `string` | _[새 이메일]_ |
| `profile.bio` | `string` | _[새 자기소개]_ |

**Request**:
```bash
# 이름만 업데이트 / Update only name
curl -X PATCH http://localhost:3000/api/users/user_123 \
  -H "Content-Type: application/json" \
  -H "X-API-Key: your-api-key" \
  -d '{
    "name": "John Updated"
  }'
```

**Response** `200 OK`: _[Updated user object]_

---

#### `DELETE /users/:id`

_[사용자 삭제]_
_[Delete a user]_

**Path Parameters**:
| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | `string` | _[사용자 ID]_ |

**Request**:
```bash
curl -X DELETE http://localhost:3000/api/users/user_123 \
  -H "X-API-Key: your-api-key"
```

**Response** `204 No Content`:
```
(Empty response body)
```

**Status Codes**:
| Code | Description |
|------|-------------|
| 204 | User deleted successfully |
| 404 | User not found |
| 401 | Unauthorized |
| 403 | Forbidden (insufficient permissions) |

---

### Resource: Posts
<!-- 다른 리소스 예시 / Another resource example -->

#### `GET /users/:userId/posts`

_[특정 사용자의 게시물 목록 조회 (중첩 리소스)]_
_[Get posts for a specific user (nested resource)]_

**Path Parameters**:
| Parameter | Type | Description |
|-----------|------|-------------|
| `userId` | `string` | _[사용자 ID]_ |

**Query Parameters**:
| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `status` | `string` | No | `all` | _[필터: `all`, `published`, `draft`]_ |
| `page` | `integer` | No | `1` | _[페이지 번호]_ |
| `limit` | `integer` | No | `10` | _[페이지당 항목 수]_ |

**Request**:
```bash
curl "http://localhost:3000/api/users/user_123/posts?status=published"
```

**Response** `200 OK`:
```json
{
  "status": "success",
  "data": {
    "posts": [
      {
        "id": "post_789",
        "title": "My First Post",
        "content": "Post content...",
        "status": "published",
        "author_id": "user_123",
        "created_at": "2026-01-20T10:00:00Z"
      }
    ],
    "pagination": {
      "page": 1,
      "limit": 10,
      "total": 5
    }
  }
}
```

---

## Webhooks
<!-- 웹훅을 제공하는 경우 / If you provide webhooks -->

### Webhook Events

_[웹훅 이벤트 목록과 페이로드 형식]_
_[List of webhook events and payload formats]_

#### `user.created`

**Triggered when**: _[새 사용자가 생성되었을 때]_

**Payload**:
```json
{
  "event": "user.created",
  "timestamp": "2026-01-20T12:00:00Z",
  "data": {
    "id": "user_123",
    "name": "John Doe",
    "email": "john@example.com"
  }
}
```

**Headers sent**:
```
Content-Type: application/json
X-Webhook-Signature: sha256=...
X-Webhook-Event: user.created
```

---

## Rate Limiting

**Limits**:
- Authenticated requests: 1000 requests/hour
- Unauthenticated requests: 100 requests/hour

**Headers**:
```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1705752000
```

**Rate Limit Exceeded** `429 Too Many Requests`:
```json
{
  "status": "error",
  "message": "Rate limit exceeded",
  "code": "RATE_LIMIT_EXCEEDED",
  "retry_after": 3600
}
```

---

## Error Responses

### Standard Error Format

All errors follow this format:

```json
{
  "status": "error",
  "message": "Human-readable error message",
  "code": "ERROR_CODE",
  "request_id": "req_abc123",
  "timestamp": "2026-01-20T12:00:00Z"
}
```

### Error Codes

| Code | HTTP Status | Description |
|------|-------------|-------------|
| `INVALID_REQUEST` | 400 | Request validation failed |
| `UNAUTHORIZED` | 401 | Missing or invalid authentication |
| `FORBIDDEN` | 403 | Insufficient permissions |
| `NOT_FOUND` | 404 | Resource not found |
| `CONFLICT` | 409 | Resource already exists |
| `VALIDATION_ERROR` | 422 | Request body validation failed |
| `RATE_LIMIT_EXCEEDED` | 429 | Too many requests |
| `INTERNAL_ERROR` | 500 | Server error |
| `SERVICE_UNAVAILABLE` | 503 | Service temporarily unavailable |

### Validation Error Format

When validation fails (`422 Unprocessable Entity`):

```json
{
  "status": "error",
  "message": "Validation failed",
  "code": "VALIDATION_ERROR",
  "errors": [
    {
      "field": "email",
      "message": "Invalid email format",
      "code": "INVALID_FORMAT"
    },
    {
      "field": "password",
      "message": "Password must be at least 8 characters",
      "code": "TOO_SHORT",
      "constraint": {
        "min": 8,
        "provided": 5
      }
    }
  ]
}
```

---

## Pagination

All list endpoints support pagination.

**Query Parameters**:
- `page` (integer): Page number, starting from 1
- `limit` (integer): Items per page (max 100, default 10)

**Response Format**:
```json
{
  "status": "success",
  "data": {
    "items": [...],
    "pagination": {
      "page": 1,
      "limit": 10,
      "total": 42,
      "total_pages": 5,
      "has_next": true,
      "has_prev": false
    }
  }
}
```

**Link Headers** (optional):
```
Link: <https://api.example.com/users?page=2>; rel="next",
      <https://api.example.com/users?page=5>; rel="last"
```

---

## Filtering and Sorting

### Filtering

Use query parameters to filter results:

```bash
# Filter by single field
GET /posts?status=published

# Multiple filters
GET /posts?status=published&author_id=user_123

# Date ranges
GET /posts?created_after=2026-01-01&created_before=2026-01-31
```

### Sorting

Use `sort` and `order` query parameters:

```bash
# Sort by single field
GET /posts?sort=created_at&order=desc

# Multiple sort fields (comma-separated)
GET /posts?sort=status,created_at&order=asc,desc
```

---

## Request/Response Examples

### TypeScript/JavaScript (fetch)

```typescript
// GET request
const response = await fetch('http://localhost:3000/api/users', {
  headers: {
    'X-API-Key': 'your-api-key'
  }
});
const data = await response.json();

// POST request
const response = await fetch('http://localhost:3000/api/users', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-API-Key': 'your-api-key'
  },
  body: JSON.stringify({
    name: 'Jane Smith',
    email: 'jane@example.com',
    password: 'secure-password'
  })
});
const data = await response.json();
```

### Python (requests)

```python
import requests

# GET request
response = requests.get(
    'http://localhost:3000/api/users',
    headers={'X-API-Key': 'your-api-key'}
)
data = response.json()

# POST request
response = requests.post(
    'http://localhost:3000/api/users',
    headers={
        'Content-Type': 'application/json',
        'X-API-Key': 'your-api-key'
    },
    json={
        'name': 'Jane Smith',
        'email': 'jane@example.com',
        'password': 'secure-password'
    }
)
data = response.json()
```

### cURL

```bash
# GET with authentication
curl -H "X-API-Key: your-api-key" \
  http://localhost:3000/api/users

# POST with JSON body
curl -X POST http://localhost:3000/api/users \
  -H "Content-Type: application/json" \
  -H "X-API-Key: your-api-key" \
  -d '{
    "name": "Jane Smith",
    "email": "jane@example.com",
    "password": "secure-password"
  }'

# PATCH with partial update
curl -X PATCH http://localhost:3000/api/users/user_123 \
  -H "Content-Type: application/json" \
  -H "X-API-Key: your-api-key" \
  -d '{"name": "Updated Name"}'

# DELETE
curl -X DELETE http://localhost:3000/api/users/user_123 \
  -H "X-API-Key: your-api-key"
```

---

## OpenAPI Specification

For machine-readable API documentation, see:
- [OpenAPI 3.0 Spec](./openapi.yaml) (if available)
- [Swagger UI](http://localhost:3000/api-docs) (if available)

---

## Related Documents

- [API Reference](./reference.md) - Function/class API documentation
- [Authentication Guide](../guides/authentication.md) - Detailed auth setup
- [Examples](../examples/) - Usage examples
- [Rate Limiting](../guides/rate-limiting.md) - Rate limit details

---

## Notes for Template Users

<!--
템플릿 사용 시 주의사항:
Notes when using this template:

1. HTTP API가 없는 프로젝트는 이 파일을 삭제하세요
   Delete this file if your project has no HTTP API

2. 각 엔드포인트는 실제 동작하는 예시로 테스트하세요
   Test each endpoint with real working examples

3. 에러 코드는 실제 구현과 일치시키세요
   Keep error codes in sync with actual implementation

4. OpenAPI/Swagger 스펙도 함께 유지하면 좋습니다
   Consider maintaining an OpenAPI/Swagger spec alongside

5. 인증 방식, 페이지네이션, 에러 형식은 프로젝트 전체에서 일관성 유지
   Maintain consistency in auth, pagination, and error formats across all endpoints

6. 버전 관리 전략을 수립하세요 (URL 버전 vs 헤더 버전)
   Establish a versioning strategy (URL-based vs header-based)

7. 각 엔드포인트의 성능 특성도 문서화하면 좋습니다 (응답 시간, 제한사항)
   Consider documenting performance characteristics (response times, limitations)
-->
