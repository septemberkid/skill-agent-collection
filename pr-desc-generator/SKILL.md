---
name: pr-desc-generator
description: Generate clear pull request descriptions from git diff and implementation changes.
---

# PR Description Generator Skill

## Purpose

Generate concise and informative PR descriptions.

---

# Output Format

```md
## Summary
<summary>

## Changes
- <change>
- <change>

## Risks
- <risk>

## Testing
- <test>

## Migration Notes
- <note>

## Follow-ups
- <item>
```

---

# Rules

- summarize behavior changes
- mention breaking changes
- mention migration impact
- avoid implementation noise
- avoid copying git diff
