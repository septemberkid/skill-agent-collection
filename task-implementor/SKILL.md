---
name: task-implementor
description: Execute engineering tasks incrementally, safely, and within scope while preserving existing architecture and minimizing unnecessary changes.
---

# Task Implementor Skill

## Purpose

Implement engineering tasks in a controlled, maintainable, and production-oriented way.

Use this skill whenever the user:
- asks to implement a feature
- asks to fix a bug
- asks to modify existing behavior
- asks to add tests
- asks to update architecture incrementally
- asks for code changes based on a task/plan

The goal is to:
- implement only what is requested
- preserve existing architecture
- minimize regressions
- keep changes incremental
- avoid scope creep
- produce production-quality code

---

# Core Principles

Prioritize:

1. correctness
2. minimal safe change
3. maintainability
4. consistency with existing codebase
5. incremental delivery
6. observability
7. testability

Avoid:
- unnecessary rewrites
- speculative abstraction
- unrelated refactors
- architecture redesign without request
- introducing new dependencies unnecessarily

---

# Workflow

## 1. Understand the Task

Identify:
- desired behavior
- affected modules
- constraints
- dependencies
- stop condition

Summarize internally before implementation.

Example:

```text
Goal:
Add refresh token validation to JWT auth flow.
```

---

## 2. Analyze Existing Code

Inspect:
- related modules
- existing patterns
- naming conventions
- architecture boundaries
- test structure
- validation/error handling patterns

Prefer consistency over personal preference.

---

## 3. Define Minimal Implementation Scope

Separate:

### Required
- changes necessary for the task

### Avoid
- unrelated cleanup
- unrelated optimization
- unrelated refactor
- speculative improvements

---

## 4. Implement Incrementally

Prefer:
- small commits
- isolated changes
- testable steps
- reversible changes

Avoid large monolithic modifications.

---

## 5. Preserve Existing Contracts

Do not break:
- public APIs
- response formats
- DB compatibility
- event contracts
- expected side effects

Unless explicitly requested.

---

## 6. Handle Errors Explicitly

Ensure:
- proper validation
- explicit error handling
- useful error messages
- no silent failures
- consistent behavior

---

## 7. Add or Update Tests

Add tests for:
- changed behavior
- edge cases
- regression prevention
- failure scenarios

Avoid meaningless coverage inflation.

---

## 8. Validate Completion

Before finishing, verify:
- task scope completed
- no unrelated modifications
- code consistency preserved
- tests updated
- no obvious regressions introduced

---

# Implementation Priorities

Prioritize in this order:

1. correctness
2. data consistency
3. reliability
4. maintainability
5. readability
6. performance optimization
7. elegance

---

# Output Format

Use this structure:

```text
Implementation Summary:
<summary>

Changes Made:
- <change>
- <change>

Files Affected:
- <file>
- <file>

Important Decisions:
- <decision>

Risks:
- <risk>

Tests Added/Updated:
- <test>

Not Included:
- <explicitly excluded item>

Suggested Follow-up:
- <optional next task>
```

---

# Scope Control Rules

Do not:
- refactor unrelated modules
- rename unrelated code
- introduce new architecture patterns unnecessarily
- add new dependencies without need
- mix feature work with cleanup work
- modify unrelated tests
- silently change behavior

If unrelated issues are discovered:

```text
Out-of-scope issue detected:
<issue>

Recommendation:
Handle separately after current task completion.
```

---

# Engineering Rules

## API Changes

If changing APIs:
- preserve backward compatibility when possible
- validate contracts
- update error handling consistently

---

## Database Changes

If modifying DB:
- consider migration safety
- consider rollback safety
- avoid destructive changes
- avoid long locks
- prefer additive migrations

---

## Async/Event Systems

If using queues/events:
- consider idempotency
- consider retries
- consider ordering assumptions
- consider partial failure handling

---

## Frontend Changes

If UI-related:
- preserve UX consistency
- preserve loading/error states
- avoid unnecessary rerenders
- avoid state duplication

---

# Large Tasks

If task is large:
- split implementation into phases
- implement smallest usable slice first
- identify follow-up tasks separately

Example:

```text
Recommended Incremental Plan:

Phase 1:
- backend endpoint
- validation
- basic tests

Phase 2:
- UI integration
- loading/error handling

Phase 3:
- observability
- optimization
```

---

# Stop Conditions

Stop when:
- requested behavior works
- affected tests pass
- implementation scope is complete
- no additional requested work remains

Do not continue into speculative improvements.

---

# Final Response Rules

At the end, clearly distinguish:

```text
Completed:
- <done>

Not Done:
- <excluded>

Optional Follow-up:
- <future improvement>
```

Avoid implying unfinished optional work is required.
