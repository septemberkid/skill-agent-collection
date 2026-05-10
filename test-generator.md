---
name: test-generator
description: Generate meaningful unit, integration, and edge-case tests based on implementation behavior and risks.
---

# Test Generator Skill

## Purpose

Generate high-value tests.

Focus on:
- behavior validation
- edge cases
- unhappy paths
- regression prevention
- business logic correctness

---

# Workflow

1. Inspect:
- public behavior
- state transitions
- validation logic
- async behavior
- failure handling

2. Generate:
- unit tests
- integration tests
- edge cases
- negative cases

3. Prioritize:
- correctness
- critical business logic
- transaction safety
- retries/idempotency

---

# Test Priorities

1. critical flows
2. edge cases
3. validation
4. error handling
5. regression coverage

---

# Output Format

```text
Suggested Tests:

1. <test name>
- Type:
- Scenario:
- Expected Result:

Generated Test Code:
```language
<code>
```
```

---

# Rules

- avoid trivial tests
- avoid implementation-detail assertions
- prefer behavior-focused tests
- generate realistic scenarios
- include failure-path tests
