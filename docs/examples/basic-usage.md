# Basic Usage Examples

<!-- 기본 사용 예제 - 간단하고 실용적인 시작점을 제공 -->
<!-- Basic examples - Provide simple, practical starting points -->

> Simple use cases for {{project-name}}.
>
> **Navigation**: [docs/](../index.md) > examples > basic-usage

---

## Template Instructions

<!-- 💡 AI Agent Guidance / AI 에이전트 가이드 -->
<!-- Examples are the fastest way for users to understand your project -->
<!-- 예제는 사용자가 프로젝트를 이해하는 가장 빠른 방법입니다 -->

### Writing Effective Basic Examples

1. **Keep it Simple**: Each example should demonstrate ONE clear concept
2. **Make it Runnable**: Provide complete, copy-paste ready code
3. **Show Output**: Always include expected output or results
4. **Explain Context**: Brief description of what and why
5. **Minimize Dependencies**: Use only core features, avoid complex setup

### Example Structure Pattern

```markdown
## Example N: [Clear, Descriptive Title]

### Description
[1-2 sentences: What does this do? When would you use it?]

### Code
[Complete, runnable code with comments]

### Expected Output
[Exact output or behavior description]

### Explanation (Optional)
[Step-by-step breakdown for complex examples]
```

---

## Example 1: _[Use Case Name - e.g., "Hello World"]_

<!-- ✏️ REPLACE THIS EXAMPLE
     - Use your actual library/project name instead of {{project-name}}
     - Show the SIMPLEST possible usage
     - This is what users will copy-paste first
-->

### Description

<!-- 설명: 이 예제가 보여주는 것 -->
<!-- Description: What this example demonstrates -->

_[What this example demonstrates - e.g., "The simplest way to get started with {{project-name}}."]_

### Code

```typescript
// [Language] example - Replace with your actual code
// {{project-name}} 기본 사용 예제

import { something } from '{{project-name}}';

// Step 1: [What this does]
// 단계 1: [이것이 하는 일]
const result = something();

// Step 2: [What this does]
// 단계 2: [이것이 하는 일]
console.log(result);
```

### Expected Output

```
Expected output here
<!-- Example: -->
<!-- Success! Result: [...] -->
```

### Explanation

<!-- Optional: Add step-by-step explanation for beginners -->
<!-- 선택사항: 초보자를 위한 단계별 설명 추가 -->

1. **Import**: _[What are we importing and why]_
2. **Usage**: _[How we're using the imported function/class]_
3. **Result**: _[What we expect to see]_

---

## Example 2: _[Common Use Case Name - e.g., "With Configuration"]_

<!-- ✏️ SECOND EXAMPLE should show slightly more realistic usage -->

### Description

_[What this example demonstrates - e.g., "How to use {{project-name}} with custom configuration."]_

### Code

```typescript
// Common configuration pattern
// 일반적인 설정 패턴

import { something } from '{{project-name}}';

const config = {
  option1: 'value1',  // [What this option does]
  option2: true,      // [What this option does]
};

const result = something(config);
console.log(result);
```

### Expected Output

```
Expected output here
```

---

## Example 3: _[Another Common Pattern]_

<!-- ✏️ Add 2-4 basic examples total
     Focus on the most common use cases
-->

### Description

_[What this example demonstrates]_

### Code

```typescript
// [Pattern name] example
// [패턴 이름] 예제

// Your code here
```

### Expected Output

```
Expected output here
```

---

## Common Patterns Summary

<!-- Quick reference for all basic patterns -->
<!-- 모든 기본 패턴에 대한 빠른 참조 -->

| Pattern | When to Use | Example |
|---------|-------------|---------|
| _[Pattern 1]_ | _[Use case]_ | See [Example 1](#example-1-use-case-name) |
| _[Pattern 2]_ | _[Use case]_ | See [Example 2](#example-2-common-use-case-name) |
| _[Pattern 3]_ | _[Use case]_ | See [Example 3](#example-3-another-common-pattern) |

---

## Quick Start Checklist

<!-- Help users get started quickly -->
<!-- 사용자가 빠르게 시작할 수 있도록 지원 -->

- [ ] Install {{project-name}}: `npm install {{project-name}}`
- [ ] Try Example 1 (Hello World)
- [ ] Customize with your own data
- [ ] Check [API Reference](../api/reference.md) for all options
- [ ] Ready for more? See [Advanced Usage](./advanced-usage.md)

---

## Troubleshooting Basic Usage

<!-- Common beginner issues -->
<!-- 초보자가 겪는 일반적인 문제 -->

### Issue: _[Common Error]_

**Symptom**: `Error message here`

**Solution**: _[How to fix it]_

```typescript
// Incorrect:
// 잘못된 예:
const wrong = something();

// Correct:
// 올바른 예:
const correct = something(config);
```

---

## Next Steps

Ready for more complex scenarios?

- [Advanced Usage](./advanced-usage.md) - Complex patterns and integrations
- [API Reference](../api/reference.md) - Complete API documentation
- [Configuration Guide](../guides/configuration.md) - All configuration options

---

## Related Documents

<!-- Cross-links to help users navigate -->
<!-- 사용자가 탐색할 수 있도록 교차 링크 -->

- [Advanced Usage](./advanced-usage.md) - Next level examples
- [API Reference](../api/reference.md) - Detailed API docs
- [Getting Started](../guides/getting-started.md) - Installation and setup
- [Troubleshooting](../guides/troubleshooting.md) - Common issues

---

<!-- 📝 Notes for Template Users -->
<!-- REMOVE THIS SECTION when creating actual documentation -->

<details>
<summary><strong>Template Usage Guide (Remove this section)</strong></summary>

### How to Use This Template

1. **Replace Placeholders**:
   - `{{project-name}}` → Your actual project name
   - `_[Use Case Name]_` → Descriptive titles
   - Example code → Your actual working code

2. **Choose Examples Wisely**:
   - Example 1: Absolute simplest "Hello World"
   - Example 2-3: Most common real-world use cases
   - Limit to 3-5 examples (more → Advanced Usage)

3. **Test Everything**:
   - Run every code example
   - Verify output matches what's documented
   - Ensure examples are copy-paste ready

4. **Keep Updated**:
   - Update examples when API changes
   - Add new common patterns as users request them
   - Remove outdated patterns

### Example Quality Checklist

- [ ] Code is complete and runnable
- [ ] Expected output is shown
- [ ] Comments explain non-obvious parts
- [ ] No external dependencies (or minimal)
- [ ] Matches current API version
- [ ] Tested and verified working

</details>
