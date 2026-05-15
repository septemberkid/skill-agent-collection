---
name: code-reviewer
description: Review source code changes and provide actionable feedback focused on correctness, maintainability, performance, security, and architecture quality.
---

# Code Reviewer Skill

## Purpose

Review source code changes and provide high-signal engineering feedback.

Use this skill whenever the user:
- asks for code review
- asks to review git diff
- asks for architecture feedback
- asks for refactor suggestions
- asks for maintainability or performance analysis
- asks to validate implementation quality

The goal is to identify:
- bugs
- edge cases
- architectural issues
- maintainability problems
- security concerns
- performance risks
- missing tests
- unnecessary complexity

Do not give generic praise.
Focus on actionable engineering feedback.

---

# Review Workflow

## 1. Inspect Repository Changes

Run:

```bash
git status --short
git diff --stat
git diff
```

If staged changes exist:

```bash
git diff --staged
```

If needed, inspect related files for context.

---

# 2. Understand the Change

Determine:

- purpose of the change
- affected modules
- data flow impact
- API contract changes
- schema or migration impact
- runtime behavior changes
- backward compatibility risks

Do not assume intent beyond the visible code.

---

# 3. Review Areas

Evaluate the code from these perspectives.

## Correctness

Look for:
- logical bugs
- invalid assumptions
- race conditions
- missing null checks
- inconsistent state updates
- edge cases
- async issues
- transaction consistency problems

Questions:
- Can this fail silently?
- Can state become inconsistent?
- Are retries/idempotency handled?
- Are errors propagated correctly?

---

## Maintainability

Look for:
- duplicated logic
- overly large functions
- poor naming
- hidden side effects
- tight coupling
- unclear abstractions
- dead code
- premature abstraction

Prefer:
- simple flow
- explicit behavior
- composable functions
- predictable interfaces

---

## Performance

Look for:
- unnecessary allocations
- repeated DB/API calls
- N+1 queries
- blocking operations
- redundant renders
- excessive serialization
- inefficient loops

Do not suggest micro-optimizations unless meaningful.

---

## Security

Look for:
- injection risks
- unsafe deserialization
- auth bypass
- privilege escalation
- secret leakage
- missing validation
- insecure defaults
- trust boundary violations

---

## Testing

Check whether:
- critical paths are covered
- edge cases are tested
- failure scenarios exist
- integration risks are validated

Suggest tests when coverage is missing.

---

## Architecture

Evaluate:
- separation of concerns
- module boundaries
- domain ownership
- consistency with existing patterns
- scalability implications
- observability impact

Avoid unnecessary abstractions.

---

# 4. Severity Levels

Use these severities:

| Severity | Meaning |
|---|---|
| critical | likely production issue or security risk |
| high | major correctness or architectural risk |
| medium | maintainability or reliability issue |
| low | minor improvement or cleanup |

Only mark issues as critical/high when justified.

---

# 5. Output Format

Use this structure:

```text
Summary:
<short overall assessment>

Findings:

1. [severity] <title>
- Problem:
- Why it matters:
- Suggested fix:

2. [severity] <title>
- Problem:
- Why it matters:
- Suggested fix:

Positive Notes:
- <good implementation detail>
- <good implementation detail>

Suggested Follow-ups:
- <optional improvement>
- <optional improvement>
```

---

# Review Rules

- Be direct and technical
- Avoid generic praise
- Avoid nitpicks unless meaningful
- Prefer actionable feedback
- Explain why something is problematic
- Include concrete fixes when possible
- Respect existing architecture unless there is a strong reason not to
- Do not invent nonexistent issues
- Do not recommend rewrites without justification

---

# Review Priorities

Prioritize findings in this order:

1. correctness
2. security
3. data consistency
4. reliability
5. maintainability
6. performance
7. style

Style issues should be low priority unless they reduce readability significantly.

---

# Special Cases

## Large Diffs

If the diff is large:

- review by module or feature area
- prioritize risky areas first
- summarize repetitive findings

---

## Mixed Changes

If unrelated concerns are mixed together:

```text
This change should likely be split into multiple commits/features because:
- database migration changes
- API contract updates
- refactor-only changes
- test-only changes
```

---

## Missing Context

If review confidence is limited:

```text
I cannot fully validate this behavior without:
- runtime context
- schema definition
- upstream API contract
- related service implementation
```

Avoid pretending certainty.
