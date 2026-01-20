# API Reference

> Complete API documentation for {{project-name}}.
>
> **Navigation**: [docs/](../index.md) > api > reference

---

## Template Instructions

<!--
이 템플릿은 다양한 유형의 API를 문서화할 수 있도록 설계되었습니다.
This template is designed to document various types of APIs.

프로젝트 유형에 따라 필요한 섹션만 사용하세요:
Use only the sections relevant to your project type:

- Library/SDK: Functions, Classes, Types 섹션 사용
- CLI Tool: CLI Commands 섹션 사용
- REST API: endpoints.md 참조 (HTTP 엔드포인트 전용)
- Composite: 여러 섹션 조합

각 섹션의 예시를 참고하여 프로젝트에 맞게 수정하세요.
Refer to examples in each section and adapt them to your project.
-->

---

## Overview

_[프로젝트의 API에 대한 간략한 설명을 작성하세요]_
_[Brief description of your API: what it provides, main use cases, key capabilities]_

**API Type**: _[Library / CLI / Hybrid / etc.]_

**Language/Framework**: _[TypeScript / Python / Go / etc.]_

**Installation**:
```bash
# 설치 명령어를 작성하세요 / Add installation command
npm install {{project-name}}
# or
pip install {{project-name}}
```

**Quick Start**:
```typescript
// 가장 기본적인 사용 예시를 보여주세요
// Show the most basic usage example
import { mainFunction } from '{{project-name}}';

const result = mainFunction();
```

---

## API Patterns

<!-- 이 섹션에서는 프로젝트 유형별로 필요한 패턴을 선택하세요 -->
<!-- Choose the patterns relevant to your project type -->

---

## Functions API
<!-- 라이브러리/SDK 프로젝트인 경우 사용 / Use for library/SDK projects -->

### Function: `functionName`

<!-- 함수의 목적과 사용 시나리오를 설명하세요 -->
<!-- Describe the function's purpose and usage scenarios -->

_[이 함수가 무엇을 하는지, 언제 사용하는지 설명]_
_[What this function does and when to use it]_

**Signature**:
```typescript
function functionName(
  param1: Type1,
  param2?: Type2,
  options?: OptionsType
): Promise<ReturnType>
```

**Parameters**:
| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| `param1` | `Type1` | Yes | - | _[매개변수 설명]_ |
| `param2` | `Type2` | No | `undefined` | _[선택적 매개변수 설명]_ |
| `options` | `OptionsType` | No | `{}` | _[옵션 객체 설명]_ |

**Returns**: `Promise<ReturnType>` - _[반환값 설명]_

**Throws**:
- `ErrorType1` - _[에러가 발생하는 조건]_
- `ErrorType2` - _[다른 에러 조건]_

**Example**:
```typescript
// 기본 사용 / Basic usage
const result = await functionName(value1);

// 옵션과 함께 사용 / With options
const result = await functionName(value1, value2, {
  option1: true,
  option2: 'custom'
});

// 에러 처리 / Error handling
try {
  const result = await functionName(value1);
} catch (error) {
  if (error instanceof ErrorType1) {
    // Handle specific error
  }
}
```

**See Also**:
- [Related function](#related-function)
- [Usage example](../examples/basic-usage.md)

---

### Function: `asyncOperation`

_[비동기 작업을 수행하는 함수 예시]_
_[Example of an async function]_

**Signature**:
```typescript
async function asyncOperation<T>(
  input: T,
  callback?: (progress: number) => void
): Promise<Result<T>>
```

**Type Parameters**:
| Name | Constraint | Description |
|------|------------|-------------|
| `T` | `Serializable` | _[제네릭 타입 설명]_ |

**Parameters**:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| `input` | `T` | Yes | _[입력 데이터]_ |
| `callback` | `(progress: number) => void` | No | _[진행 상황 콜백]_ |

**Returns**: `Promise<Result<T>>` - _[처리 결과]_

**Example**:
```typescript
// 진행 상황 추적과 함께 사용 / With progress tracking
const result = await asyncOperation(data, (progress) => {
  console.log(`Processing: ${progress}%`);
});
```

---

## Classes API
<!-- 클래스 기반 API인 경우 사용 / Use for class-based APIs -->

### Class: `ClassName`

_[클래스의 목적과 주요 기능 설명]_
_[Purpose and main functionality of the class]_

**Constructor**:
```typescript
constructor(options: ClassOptions)
```

**Constructor Parameters**:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| `options` | `ClassOptions` | Yes | _[설정 옵션]_ |
| `options.prop1` | `string` | Yes | _[필수 옵션]_ |
| `options.prop2` | `number` | No | _[선택적 옵션]_ |

**Properties**:
| Property | Type | Readonly | Description |
|----------|------|----------|-------------|
| `prop1` | `string` | Yes | _[읽기 전용 속성]_ |
| `prop2` | `number` | No | _[수정 가능 속성]_ |
| `state` | `StateType` | Yes | _[현재 상태]_ |

**Methods**:

#### `method1(arg: string): Promise<void>`

_[메서드 설명]_

**Parameters**:
| Name | Type | Description |
|------|------|-------------|
| `arg` | `string` | _[인자 설명]_ |

**Returns**: `Promise<void>`

**Example**:
```typescript
await instance.method1('value');
```

#### `method2(options: MethodOptions): Result`

_[다른 메서드 설명]_

**Parameters**:
| Name | Type | Description |
|------|------|-------------|
| `options` | `MethodOptions` | _[옵션 설명]_ |

**Returns**: `Result` - _[반환값 설명]_

**Static Methods**:

#### `ClassName.create(config: Config): ClassName`

_[팩토리 메서드 설명]_
_[Factory method description]_

**Full Usage Example**:
```typescript
// 인스턴스 생성 / Create instance
const instance = new ClassName({
  prop1: 'required value',
  prop2: 42
});

// 또는 팩토리 메서드 사용 / Or use factory method
const instance = ClassName.create(config);

// 메서드 호출 / Call methods
await instance.method1('arg');
const result = instance.method2({ option: true });

// 속성 접근 / Access properties
console.log(instance.state);
```

---

## CLI Commands
<!-- CLI 도구인 경우 사용 / Use for CLI tools -->

### Command: `{{project-name}} command`

_[명령어 설명]_
_[Command description]_

**Syntax**:
```bash
{{project-name}} command [options] <required-arg> [optional-arg]
```

**Arguments**:
| Argument | Required | Description |
|----------|----------|-------------|
| `required-arg` | Yes | _[필수 인자 설명]_ |
| `optional-arg` | No | _[선택적 인자 설명]_ |

**Options**:
| Flag | Alias | Type | Default | Description |
|------|-------|------|---------|-------------|
| `--option` | `-o` | `string` | - | _[옵션 설명]_ |
| `--verbose` | `-v` | `boolean` | `false` | _[상세 출력]_ |
| `--config` | `-c` | `path` | `./config.json` | _[설정 파일 경로]_ |

**Examples**:
```bash
# 기본 사용 / Basic usage
{{project-name}} command input.txt

# 옵션과 함께 / With options
{{project-name}} command --option value input.txt output.txt

# 상세 출력 모드 / Verbose mode
{{project-name}} command -v input.txt

# 파이프와 함께 사용 / With pipes
cat input.txt | {{project-name}} command - > output.txt
```

**Exit Codes**:
| Code | Meaning |
|------|---------|
| 0 | Success |
| 1 | General error |
| 2 | Invalid arguments |
| 3 | File not found |

---

### Command: `{{project-name}} init`

_[초기화 명령어 예시]_
_[Initialization command example]_

**Syntax**:
```bash
{{project-name}} init [directory] [options]
```

**Arguments**:
| Argument | Required | Default | Description |
|----------|----------|---------|-------------|
| `directory` | No | `.` | _[초기화할 디렉토리]_ |

**Options**:
| Flag | Type | Default | Description |
|------|------|---------|-------------|
| `--template` | `string` | `default` | _[사용할 템플릿]_ |
| `--force` | `boolean` | `false` | _[기존 파일 덮어쓰기]_ |

**Interactive Prompts**:
1. Project name: _[프로젝트 이름 입력]_
2. Template selection: _[템플릿 선택]_
3. Configuration options: _[설정 옵션]_

**Example**:
```bash
# 대화형 초기화 / Interactive init
{{project-name}} init

# 템플릿 지정 / With template
{{project-name}} init my-project --template advanced

# 자동 모드 / Non-interactive
{{project-name}} init my-project --template default --force
```

---

## Types & Interfaces
<!-- 타입 정의 섹션 / Type definitions section -->

### Core Types

#### `MainConfigType`

_[주요 설정 타입 설명]_
_[Main configuration type description]_

```typescript
interface MainConfigType {
  /**
   * 필수 설정 항목
   * Required configuration field
   */
  requiredField: string;

  /**
   * 선택적 설정 항목
   * Optional configuration field
   * @default 'default-value'
   */
  optionalField?: string;

  /**
   * 숫자 범위 제한
   * Numeric value with constraints
   * @minimum 0
   * @maximum 100
   */
  numericField: number;

  /**
   * 중첩된 객체
   * Nested object configuration
   */
  nested: {
    prop1: boolean;
    prop2: string[];
  };
}
```

**Usage**:
```typescript
const config: MainConfigType = {
  requiredField: 'value',
  numericField: 50,
  nested: {
    prop1: true,
    prop2: ['item1', 'item2']
  }
};
```

---

#### `Result<T>`

_[제네릭 결과 타입]_
_[Generic result type]_

```typescript
type Result<T> =
  | { success: true; data: T }
  | { success: false; error: Error };
```

**Type Guards**:
```typescript
function isSuccess<T>(result: Result<T>): result is { success: true; data: T } {
  return result.success === true;
}

// 사용 예시 / Usage
const result = await someOperation();
if (isSuccess(result)) {
  console.log(result.data); // Type-safe access
} else {
  console.error(result.error);
}
```

---

#### `OptionsType`

_[공통 옵션 타입]_
_[Common options type]_

```typescript
interface OptionsType {
  /**
   * 타임아웃 (밀리초)
   * Timeout in milliseconds
   * @default 5000
   */
  timeout?: number;

  /**
   * 재시도 횟수
   * Number of retry attempts
   * @default 3
   */
  retries?: number;

  /**
   * 로깅 활성화
   * Enable logging
   * @default false
   */
  verbose?: boolean;

  /**
   * 커스텀 핸들러
   * Custom error handler
   */
  onError?: (error: Error) => void;
}
```

---

### Enums

#### `StatusEnum`

_[상태 열거형]_
_[Status enumeration]_

```typescript
enum StatusEnum {
  /** 초기 상태 / Initial state */
  Idle = 'idle',

  /** 처리 중 / Processing */
  Processing = 'processing',

  /** 완료 / Completed */
  Complete = 'complete',

  /** 실패 / Failed */
  Failed = 'failed'
}
```

**Usage**:
```typescript
let status: StatusEnum = StatusEnum.Idle;

if (status === StatusEnum.Processing) {
  // Handle processing state
}
```

---

### Type Utilities

#### `Partial<T>`, `Required<T>`, `Pick<T, K>`

_[타입스크립트 유틸리티 타입 활용 예시]_
_[TypeScript utility type usage examples]_

```typescript
// 모든 필드를 선택적으로 / All fields optional
type PartialConfig = Partial<MainConfigType>;

// 모든 필드를 필수로 / All fields required
type RequiredConfig = Required<MainConfigType>;

// 특정 필드만 선택 / Pick specific fields
type MinimalConfig = Pick<MainConfigType, 'requiredField'>;
```

---

## Error Handling

### Error Types

#### `ValidationError`

```typescript
class ValidationError extends Error {
  constructor(
    message: string,
    public field: string,
    public value: unknown
  ) {
    super(message);
    this.name = 'ValidationError';
  }
}
```

**When thrown**: _[에러가 발생하는 상황]_

**Example**:
```typescript
try {
  validateInput(data);
} catch (error) {
  if (error instanceof ValidationError) {
    console.error(`Invalid ${error.field}: ${error.value}`);
  }
}
```

---

#### `OperationError`

```typescript
class OperationError extends Error {
  constructor(
    message: string,
    public code: string,
    public retryable: boolean = false
  ) {
    super(message);
    this.name = 'OperationError';
  }
}
```

**Error Codes**:
| Code | Retryable | Description |
|------|-----------|-------------|
| `TIMEOUT` | Yes | _[작업 시간 초과]_ |
| `INVALID_STATE` | No | _[잘못된 상태]_ |
| `RESOURCE_NOT_FOUND` | No | _[리소스를 찾을 수 없음]_ |

---

## Advanced Usage

### Generic Functions

```typescript
function transform<TInput, TOutput>(
  input: TInput,
  transformer: (item: TInput) => TOutput
): TOutput {
  return transformer(input);
}

// 사용 예시 / Usage
const result = transform<string, number>('123', (str) => parseInt(str));
```

---

### Async Iterators

```typescript
async function* generateItems(): AsyncIterableIterator<Item> {
  // 비동기 이터레이터 구현
  // Async iterator implementation
}

// 사용 예시 / Usage
for await (const item of generateItems()) {
  console.log(item);
}
```

---

### Middleware Pattern

```typescript
type Middleware<T> = (
  context: T,
  next: () => Promise<void>
) => Promise<void>;

function useMiddleware<T>(
  middlewares: Middleware<T>[]
): (context: T) => Promise<void> {
  // 미들웨어 체인 구현
  // Middleware chain implementation
}
```

---

## Related Documents

- [REST API Endpoints](./endpoints.md) - HTTP API documentation
- [Basic Examples](../examples/basic-usage.md) - Getting started examples
- [Advanced Examples](../examples/advanced-usage.md) - Complex usage patterns
- [Architecture](../architecture/) - System architecture
- [Type Definitions](../../src/types/) - Source code type definitions

---

## Notes for Template Users

<!--
템플릿 사용 시 주의사항:
Notes when using this template:

1. 프로젝트 유형에 맞는 섹션만 유지하세요
   Keep only sections relevant to your project type

2. {{project-name}}을 실제 프로젝트 이름으로 교체하세요
   Replace {{project-name}} with your actual project name

3. 예시 코드는 실제 작동하는 코드로 교체하세요
   Replace example code with actual working code

4. 타입 정의는 실제 소스 코드와 동기화하세요
   Keep type definitions in sync with actual source code

5. 모든 public API는 문서화되어야 합니다
   All public APIs should be documented

6. JSDoc 주석을 활용하여 IDE 자동완성을 지원하세요
   Use JSDoc comments to support IDE autocompletion
-->
