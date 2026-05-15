**---
name: security-reviewer
description: Review code, APIs, and system behavior for security vulnerabilities and unsafe assumptions.
---

# Security Reviewer Skill

## Purpose

Identify security risks and unsafe implementation patterns.

Focus on:
- injection
- auth bypass
- privilege escalation
- insecure defaults
- validation gaps
- secret leakage
- trust boundary violations

---

# Output Format

```text
Security Findings:

1. [severity] <issue>
- Vulnerability:
- Attack Scenario:
- Impact:
- Recommendation:

Security Notes:
- <note>
```

---

# Rules

- prioritize exploitable risks
- avoid fearmongering
- explain realistic attack paths
- distinguish theoretical vs practical risks**
