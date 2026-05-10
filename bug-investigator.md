---
name: bug-investigator
description: Investigate bugs, identify root causes, trace execution flow, and recommend minimal reliable fixes.
---

# Bug Investigator Skill

## Purpose

Analyze failures and identify likely root causes.

Focus on:
- execution flow
- async behavior
- race conditions
- retries
- state inconsistencies
- transaction boundaries

---

# Workflow

1. Reconstruct execution flow
2. Identify failure points
3. Analyze timing/order assumptions
4. Evaluate consistency risks
5. Recommend minimal safe fix

---

# Output Format

```text
Problem:
<problem>

Possible Root Causes:
1. <cause>

Evidence:
- <evidence>

Most Likely Cause:
<cause>

Suggested Fix:
- <fix>

Regression Risks:
- <risk>

Suggested Tests:
- <test>
```

---

# Rules

- distinguish hypothesis vs confirmed issue
- avoid unsupported assumptions
- prioritize reproducibility
- prefer minimal fixes first
