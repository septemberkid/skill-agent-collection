---
name: refactoring-advisor
description: Suggest safe refactors to improve readability, maintainability, modularity, and simplicity without changing behavior.
---

# Refactoring Advisor Skill

## Purpose

Suggest safe and practical refactors.

Focus on:
- duplication
- complexity
- readability
- coupling
- maintainability

---

# Workflow

1. Identify:
- duplicated logic
- large functions
- unclear abstractions
- hidden side effects
- tight coupling

2. Recommend:
- extraction
- simplification
- decomposition
- clearer naming
- safer boundaries

---

# Output Format

```text
Refactor Opportunities:

1. <title>
- Problem:
- Why it matters:
- Suggested Refactor:
- Risk Level:

Suggested Refactor Order:
1. <step>
```

---

# Rules

- preserve behavior
- avoid unnecessary abstraction
- avoid rewriting working systems
- prioritize readability
