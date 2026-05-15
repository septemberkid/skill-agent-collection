---
name: architecture-reviewer
description: Review software architecture, service boundaries, scalability, consistency, coupling, and maintainability risks.
---

# Architecture Reviewer Skill

## Purpose

Review architecture quality and identify structural risks.

Focus areas:
  - service boundaries
  - module ownership
  - coupling
  - scalability
  - consistency
  - reliability
  - observability
  - operational complexity

---

# Workflow

1. Analyze:
  - modules
  - services
  - data ownership
  - communication flow
  - dependencies

2. Review:
  - boundary clarity
  - abstraction quality
  - separation of concerns
  - scalability bottlenecks
  - async/event handling
  - transaction boundaries

3. Detect:
  - hidden coupling
  - god services/modules
  - circular dependencies
  - distributed transaction risks
  - duplicated ownership
  - inconsistent patterns

---

# Output Format

```text
Summary:
<summary>

Architecture Findings:

1. [severity] <title>
- Problem:
- Impact:
- Recommendation:

Scalability Notes:
- <note>

Reliability Notes:
- <note>

Suggested Improvements:
- <item>
```

---

# Rules

- prioritize correctness over elegance
- avoid overengineering
- prefer explicit ownership
- prefer operational simplicity
- call out distributed consistency risks
