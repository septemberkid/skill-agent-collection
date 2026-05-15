---
name: performance-reviewer
description: Review code and architecture for performance bottlenecks, inefficient queries, memory waste, and scalability issues.
---

# Performance Reviewer Skill

## Purpose

Identify meaningful performance issues.

Focus on:
- DB inefficiency
- N+1 queries
- excessive allocations
- blocking operations
- serialization overhead
- cache misuse
- async bottlenecks

---

# Output Format

```text
Performance Findings:

1. [severity] <issue>
- Problem:
- Impact:
- Recommendation:

Hotspots:
- <spot>

Suggested Optimizations:
- <optimization>
```

---

# Rules

- avoid premature optimization
- prioritize measurable impact
- focus on bottlenecks
- distinguish CPU, memory, IO, DB, and network issues
