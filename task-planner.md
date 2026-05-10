---
name: task-planner
description: Break down engineering work into clear, sequential, scoped tasks with dependencies, priorities, risks, and execution phases.
---

# Task Planner Skill

## Purpose

Convert vague engineering requests into actionable implementation plans.

Use this skill whenever the user:
- asks how to implement something
- asks for project/task breakdown
- asks for execution planning
- asks for roadmap/phasing
- asks for incremental implementation strategy
- asks what should be done first

The goal is to create:
- clear scope
- execution order
- manageable tasks
- realistic implementation phases
- dependency visibility
- risk awareness

---

# Planning Principles

Prioritize:
1. smallest working solution
2. low-risk implementation
3. incremental delivery
4. maintainability
5. fast validation feedback

Avoid:
- overengineering
- premature abstraction
- large rewrites
- mixing unrelated concerns

---

# Workflow

## 1. Understand the Goal

Identify:
- business goal
- technical goal
- success criteria
- constraints
- affected systems

Summarize in one sentence.

Example:

```text
Goal:
Implement OAuth login using Google for existing users.
```

---

## 2. Define Scope

Separate:

### In Scope
- required work

### Out of Scope
- unrelated or future improvements

---

## 3. Identify Work Areas

Break work into domains:

Examples:
- backend
- frontend
- database
- infra
- auth
- testing
- observability
- deployment

---

## 4. Create Execution Phases

Prefer incremental phases.

Example:

```text
Phase 1:
- add OAuth endpoint
- validate token
- create user mapping

Phase 2:
- frontend login button
- session persistence

Phase 3:
- audit logging
- retry handling
```

Each phase should produce usable progress.

---

## 5. Break Into Tasks

Each task should be:
- small
- testable
- independently understandable

Good task example:

```text
Add JWT verification middleware for protected routes
```

Bad task example:

```text
Improve authentication system
```

---

## 6. Define Dependencies

Explicitly identify:

```text
Dependencies:
- user table must support oauth_provider
- JWT middleware required before protected endpoints
```

---

## 7. Identify Risks

Examples:
- migration risk
- backward compatibility
- transaction consistency
- rollout risk
- auth/session invalidation
- performance bottleneck

---

## 8. Define Done Criteria

Each phase/task should have measurable completion.

Example:

```text
Done when:
- OAuth login succeeds
- existing users can link account
- protected routes validate JWT
- tests pass
```

---

# Output Format

Use this structure:

```text
Goal:
<goal>

In Scope:
- <item>

Out of Scope:
- <item>

Execution Plan:

Phase 1:
- <task>
- <task>

Phase 2:
- <task>
- <task>

Dependencies:
- <dependency>

Risks:
- <risk>

Recommended Order:
1. <step>
2. <step>

Done Criteria:
- <criteria>
```

---

# Planning Rules

- Prefer vertical slices over layered implementation
- Prefer shipping usable increments
- Keep tasks implementation-oriented
- Avoid vague tasks
- Avoid assigning multiple concerns to one task
- Separate refactor from feature work
- Separate migration from feature rollout when possible
- Prefer reversible changes
- Prefer backward-compatible rollout

---

# Special Cases

## Large Features

If the feature is large:
- recommend MVP first
- identify optional improvements separately

---

## Refactor Requests

For refactors:
- define safety boundaries
- identify regression risks
- recommend test coverage first

---

## Unknown Requirements

If requirements are unclear:
- identify assumptions
- ask only blocking clarification questions
- continue planning using explicit assumptions
