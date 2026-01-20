# Advanced Usage Examples

<!-- 고급 사용 예제 - 복잡한 시나리오와 통합 패턴 -->
<!-- Advanced examples - Complex scenarios and integration patterns -->

> Complex scenarios and advanced patterns for {{project-name}}.
>
> **Navigation**: [docs/](../index.md) > examples > advanced-usage

---

## Template Instructions

<!-- 💡 AI Agent Guidance / AI 에이전트 가이드 -->
<!-- Advanced examples show real-world integration and complex patterns -->
<!-- 고급 예제는 실제 통합 및 복잡한 패턴을 보여줍니다 -->

### Writing Effective Advanced Examples

1. **Show Real Integration**: Demonstrate how {{project-name}} works with other tools/frameworks
2. **Explain Trade-offs**: Document why you'd choose one approach over another
3. **Include Performance**: Show optimization techniques and benchmarks when relevant
4. **Provide Full Context**: Include setup, configuration, and error handling
5. **Link to Basics**: Reference basic examples for foundational concepts

### Advanced Example Structure Pattern

```markdown
## Example N: [Specific, Technical Title]

### Description
[What problem this solves, when you'd use this pattern]

### Prerequisites
[Dependencies, setup, knowledge required]

### Full Code
[Complete, production-ready example with error handling]

### Expected Output / Behavior
[Results, performance characteristics]

### Explanation
[Why this approach, alternatives, trade-offs]

### Performance Considerations (if applicable)
[Benchmarks, optimization tips]

### Common Pitfalls
[What to avoid, troubleshooting]
```

---

## Example 1: _[Advanced Use Case - e.g., "Integration with Express.js"]_

<!-- ✏️ REPLACE THIS EXAMPLE
     - Show realistic, production-ready code
     - Include error handling and edge cases
     - Explain WHY this pattern is needed
-->

### Description

<!-- 설명: 이 예제가 해결하는 문제 -->
<!-- Description: What problem this example solves -->

_[What this example demonstrates - e.g., "How to integrate {{project-name}} into an Express.js API with proper error handling and middleware patterns."]_

### Prerequisites

<!-- 사전 요구사항: 이 예제를 실행하기 위해 필요한 것 -->
<!-- Prerequisites: What's needed to run this example -->

- _[Prerequisite 1 - e.g., "Node.js 18+ and Express.js installed"]_
- _[Prerequisite 2 - e.g., "Understanding of Express middleware"]_
- _[Prerequisite 3 - e.g., "Familiarity with async/await patterns"]_

### Installation

```bash
npm install {{project-name}} express
# Add any other required packages
```

### Full Code

```typescript
// Production-ready integration example
// 프로덕션 준비된 통합 예제

import express from 'express';
import { something, SomeConfig, ErrorHandler } from '{{project-name}}';

// Step 1: Initialize with configuration
// 단계 1: 설정으로 초기화
const config: SomeConfig = {
  option1: process.env.OPTION_1 || 'default',
  option2: true,
  timeout: 5000,
};

const instance = new something(config);

// Step 2: Create Express app
// 단계 2: Express 앱 생성
const app = express();
app.use(express.json());

// Step 3: Middleware for {{project-name}}
// 단계 3: {{project-name}}용 미들웨어
app.use(async (req, res, next) => {
  try {
    // Attach instance to request
    // 요청에 인스턴스 첨부
    req.limiter = instance;
    next();
  } catch (error) {
    next(error);
  }
});

// Step 4: Route handler using {{project-name}}
// 단계 4: {{project-name}}를 사용하는 라우트 핸들러
app.post('/api/process', async (req, res, next) => {
  try {
    const { data } = req.body;

    // Validate input
    // 입력 검증
    if (!data) {
      return res.status(400).json({ error: 'Missing data field' });
    }

    // Process with {{project-name}}
    // {{project-name}}로 처리
    const result = await req.limiter.process(data);

    // Return result
    // 결과 반환
    res.json({
      success: true,
      result,
      timestamp: new Date().toISOString(),
    });
  } catch (error) {
    next(error);
  }
});

// Step 5: Error handling middleware
// 단계 5: 에러 처리 미들웨어
app.use((error: Error, req, res, next) => {
  console.error('Error:', error);

  if (error instanceof ErrorHandler) {
    return res.status(error.statusCode).json({
      error: error.message,
      code: error.code,
    });
  }

  res.status(500).json({
    error: 'Internal server error',
  });
});

// Step 6: Start server
// 단계 6: 서버 시작
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

### Expected Output

**Request:**
```bash
curl -X POST http://localhost:3000/api/process \
  -H "Content-Type: application/json" \
  -d '{"data": "test input"}'
```

**Response:**
```json
{
  "success": true,
  "result": {
    "processed": "test input",
    "status": "completed"
  },
  "timestamp": "2026-01-20T10:30:00.000Z"
}
```

### Explanation

<!-- 설명: 이 패턴이 작동하는 방식 -->
<!-- Explanation: How this pattern works -->

1. **Configuration**: _[Why we initialize outside request handlers]_
2. **Middleware Pattern**: _[Benefits of attaching to request object]_
3. **Error Handling**: _[How errors propagate through Express]_
4. **Async/Await**: _[Why we use async handlers]_

### Performance Considerations

<!-- 성능 고려사항 -->
<!-- Performance considerations -->

- **Instance Reuse**: _[Why we create one instance vs per-request]_
- **Timeout Settings**: _[How to tune timeout for your use case]_
- **Memory Usage**: _[Expected memory footprint]_

**Benchmark** (if applicable):
```
Requests/sec: 1000
Avg latency: 45ms
P95 latency: 120ms
```

### Common Pitfalls

<!-- 일반적인 함정 -->
<!-- Common pitfalls -->

1. **Creating Instance Per Request**: ⚠️ Don't do this - creates memory leaks
   ```typescript
   // ❌ Wrong:
   app.post('/api/process', async (req, res) => {
     const instance = new something(config); // Memory leak!
     // ...
   });

   // ✅ Correct: Reuse instance (shown in main example)
   ```

2. **Missing Error Handling**: Always use try/catch or error middleware
3. **Blocking Operations**: Use async/await, don't block event loop

---

## Example 2: _[Another Advanced Pattern - e.g., "Batch Processing with Concurrency Control"]_

<!-- ✏️ Show different complexity dimension -->

### Description

_[What this example demonstrates - e.g., "How to process large datasets efficiently using {{project-name}} with concurrency limits and progress tracking."]_

### Prerequisites

- _[Requirements]_

### Full Code

```typescript
// Batch processing with concurrency control
// 동시성 제어가 있는 배치 처리

import { something, BatchProcessor } from '{{project-name}}';
import pLimit from 'p-limit';

async function processBatch(items: string[], options = {}) {
  const {
    concurrency = 5,
    onProgress = () => {},
  } = options;

  // Limit concurrent operations
  // 동시 작업 제한
  const limit = pLimit(concurrency);

  const processor = new something({
    batchSize: 100,
    timeout: 10000,
  });

  let completed = 0;
  const total = items.length;

  // Process with concurrency control
  // 동시성 제어로 처리
  const results = await Promise.all(
    items.map((item) =>
      limit(async () => {
        try {
          const result = await processor.process(item);
          completed++;
          onProgress({ completed, total, percentage: (completed / total) * 100 });
          return { success: true, item, result };
        } catch (error) {
          completed++;
          onProgress({ completed, total, percentage: (completed / total) * 100 });
          return { success: false, item, error: error.message };
        }
      })
    )
  );

  // Cleanup
  // 정리
  await processor.close();

  return {
    total,
    successful: results.filter(r => r.success).length,
    failed: results.filter(r => !r.success).length,
    results,
  };
}

// Usage
// 사용법
const items = Array.from({ length: 1000 }, (_, i) => `item-${i}`);

processBatch(items, {
  concurrency: 10,
  onProgress: ({ completed, total, percentage }) => {
    console.log(`Progress: ${completed}/${total} (${percentage.toFixed(1)}%)`);
  },
}).then(summary => {
  console.log('Batch processing complete:', summary);
});
```

### Expected Output

```
Progress: 10/1000 (1.0%)
Progress: 50/1000 (5.0%)
Progress: 100/1000 (10.0%)
...
Progress: 1000/1000 (100.0%)
Batch processing complete: {
  total: 1000,
  successful: 998,
  failed: 2,
  results: [...]
}
```

### Performance Tuning

<!-- 성능 튜닝 가이드 -->
<!-- Performance tuning guide -->

| Concurrency | Throughput | Memory Usage | Recommended For |
|-------------|------------|--------------|-----------------|
| 5 (default) | ~100/sec | Low | Small datasets |
| 10 | ~200/sec | Medium | Medium datasets |
| 20+ | ~400/sec | High | Large datasets, powerful servers |

---

## Example 3: _[Integration Pattern - e.g., "With TypeScript and Type Guards"]_

### Description

_[Show how to use {{project-name}} with full type safety]_

### Full Code

```typescript
// Full TypeScript integration with type guards
// 타입 가드를 사용한 완전한 TypeScript 통합

import { something, Result, ErrorType } from '{{project-name}}';

// Define custom types
// 커스텀 타입 정의
interface UserData {
  id: string;
  name: string;
  email: string;
}

interface ProcessedResult {
  userId: string;
  status: 'success' | 'failed';
  data?: unknown;
  error?: string;
}

// Type guard for result validation
// 결과 검증을 위한 타입 가드
function isValidResult(result: unknown): result is Result {
  return (
    typeof result === 'object' &&
    result !== null &&
    'status' in result
  );
}

// Type-safe processing function
// 타입 안전 처리 함수
async function processUser(user: UserData): Promise<ProcessedResult> {
  const processor = something<UserData>();

  try {
    const result = await processor.process(user);

    if (!isValidResult(result)) {
      throw new Error('Invalid result format');
    }

    return {
      userId: user.id,
      status: 'success',
      data: result,
    };
  } catch (error) {
    return {
      userId: user.id,
      status: 'failed',
      error: error instanceof Error ? error.message : 'Unknown error',
    };
  }
}
```

---

## Best Practices

<!-- 모범 사례 - 실전 경험에서 나온 패턴 -->
<!-- Best practices - Patterns from real-world experience -->

### 1. **Error Handling**

<!-- 에러 처리: 항상 예상 및 예상치 못한 오류 처리 -->
<!-- Error handling: Always handle expected and unexpected errors -->

```typescript
// ✅ Good: Comprehensive error handling
try {
  const result = await instance.process(data);
  return result;
} catch (error) {
  if (error instanceof SpecificError) {
    // Handle specific error type
  } else {
    // Handle unexpected errors
    logger.error('Unexpected error:', error);
    throw new ApplicationError('Processing failed');
  }
}
```

**Why**: _[Explanation of why this matters]_

---

### 2. **Resource Management**

<!-- 리소스 관리: 정리하고 메모리 누수 방지 -->
<!-- Resource management: Clean up and prevent memory leaks -->

```typescript
// ✅ Good: Proper cleanup
const processor = new something(config);

try {
  // Use processor
  await processor.process(data);
} finally {
  // Always cleanup
  await processor.close();
}
```

**Why**: _[Explanation of resource leaks]_

---

### 3. **Configuration Management**

<!-- 설정 관리: 환경별 설정 분리 -->
<!-- Configuration management: Separate config by environment -->

```typescript
// ✅ Good: Environment-based config
const config = {
  timeout: process.env.NODE_ENV === 'production' ? 5000 : 10000,
  retries: process.env.NODE_ENV === 'production' ? 3 : 1,
  logLevel: process.env.LOG_LEVEL || 'info',
};
```

**Why**: _[Benefits of environment-specific config]_

---

### 4. **Testing Integration**

<!-- 테스트 통합: 고급 기능 테스트 방법 -->
<!-- Testing integration: How to test advanced features -->

```typescript
// Example test setup
import { jest } from '@jest/globals';
import { something } from '{{project-name}}';

describe('Advanced usage', () => {
  let instance;

  beforeEach(() => {
    instance = new something({ testMode: true });
  });

  afterEach(async () => {
    await instance.close();
  });

  it('should handle concurrent requests', async () => {
    const promises = Array.from({ length: 10 }, (_, i) =>
      instance.process(`data-${i}`)
    );

    const results = await Promise.all(promises);
    expect(results).toHaveLength(10);
  });
});
```

---

## Performance Optimization Guide

<!-- 성능 최적화 가이드 -->
<!-- Performance optimization guide -->

### Benchmarking

```typescript
// Measure performance of different configurations
// 다양한 설정의 성능 측정

import { performance } from 'perf_hooks';

async function benchmark(config) {
  const processor = new something(config);
  const start = performance.now();

  // Run test
  await processor.process(testData);

  const end = performance.now();
  const duration = end - start;

  console.log(`Config ${JSON.stringify(config)}: ${duration}ms`);

  await processor.close();
}
```

### Optimization Checklist

- [ ] Use connection pooling for external resources
- [ ] Implement caching where appropriate
- [ ] Batch operations when possible
- [ ] Monitor memory usage in production
- [ ] Profile hot paths with performance tools
- [ ] Use streaming for large datasets

---

## Production Deployment Checklist

<!-- 프로덕션 배포 체크리스트 -->
<!-- Production deployment checklist -->

- [ ] Environment variables configured
- [ ] Error tracking integrated (Sentry, etc.)
- [ ] Logging configured appropriately
- [ ] Resource limits set (timeouts, max connections)
- [ ] Health check endpoints implemented
- [ ] Metrics/monitoring in place
- [ ] Graceful shutdown handlers
- [ ] Load tested at expected scale

---

## Common Advanced Patterns Summary

<!-- 일반적인 고급 패턴 요약 -->
<!-- Common advanced patterns summary -->

| Pattern | Use Case | Complexity | Example |
|---------|----------|------------|---------|
| Middleware Integration | Web frameworks | Medium | [Example 1](#example-1-advanced-use-case) |
| Batch Processing | Large datasets | High | [Example 2](#example-2-another-advanced-pattern) |
| Type Safety | TypeScript projects | Medium | [Example 3](#example-3-integration-pattern) |
| _[Custom Pattern]_ | _[Use case]_ | _[Level]_ | _[Link]_ |

---

## Troubleshooting Advanced Scenarios

<!-- 고급 시나리오 문제 해결 -->
<!-- Troubleshooting advanced scenarios -->

### Issue: Memory Leaks in Long-Running Processes

**Symptom**: Memory usage grows over time

**Diagnosis**:
```typescript
// Monitor memory usage
console.log(process.memoryUsage());
```

**Solution**: _[How to fix - proper cleanup, instance reuse, etc.]_

---

### Issue: Performance Degradation Under Load

**Symptom**: Response times increase with concurrent requests

**Diagnosis**: Use profiling tools (clinic.js, 0x)

**Solution**: _[Implement connection pooling, adjust concurrency, etc.]_

---

## Further Reading

<!-- 추가 읽기 자료 -->
<!-- Further reading -->

- [Architecture Overview](../architecture/overview.md) - Understand internal design
- [Performance Tuning](../guides/performance.md) - Detailed optimization guide
- [API Reference](../api/reference.md) - Complete API documentation
- [Basic Usage](./basic-usage.md) - Review fundamentals

---

## Related Documents

<!-- Cross-links -->
<!-- 교차 링크 -->

- [Basic Usage](./basic-usage.md) - Start with fundamentals
- [API Reference](../api/reference.md) - Detailed API docs
- [Architecture Overview](../architecture/overview.md) - System design
- [Configuration Guide](../guides/configuration.md) - All config options
- [Troubleshooting](../guides/troubleshooting.md) - Common issues

---

<!-- 📝 Notes for Template Users -->
<!-- REMOVE THIS SECTION when creating actual documentation -->

<details>
<summary><strong>Template Usage Guide (Remove this section)</strong></summary>

### How to Use This Template

1. **Choose Real-World Examples**:
   - Integration with popular frameworks (Express, React, etc.)
   - Production patterns users actually need
   - Performance-critical scenarios
   - Complex error handling

2. **Include Complete Code**:
   - No pseudocode - real, runnable examples
   - Include imports, setup, teardown
   - Show error handling
   - Add comments in both languages

3. **Document Trade-offs**:
   - Why choose one approach over another
   - Performance implications
   - Complexity vs. benefits

4. **Test Everything**:
   - Run all examples in realistic environments
   - Benchmark performance claims
   - Verify under load

### Advanced Example Quality Checklist

- [ ] Solves real production problem
- [ ] Includes error handling
- [ ] Shows performance characteristics
- [ ] Documents prerequisites clearly
- [ ] Explains trade-offs and alternatives
- [ ] Production-ready (not toy examples)
- [ ] Tested under realistic conditions
- [ ] Links to relevant API docs

### Pattern Selection Guide

Good advanced examples show:
- Integration with popular tools/frameworks
- Handling edge cases and errors
- Performance optimization techniques
- Production deployment considerations
- Type safety and validation
- Monitoring and observability

Avoid:
- Contrived scenarios users won't encounter
- Over-engineering simple problems
- Undocumented magic/tricks
- Untested performance claims

</details>
