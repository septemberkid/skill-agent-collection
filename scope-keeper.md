---
name: scope-keeper
description: Keep agent work focused, prevent scope creep, clarify boundaries, and help the user stay aligned with the original software engineering task.
---

# Scope Keeper Skill

## Purpose

Keep the agent and user focused on the original task scope.

Use this skill whenever the user:
- asks for implementation help
- asks for multi-step engineering work
- expands the request repeatedly
- mixes unrelated requirements
- asks for "sekalian", "tambahkan juga", "while you're at it", or similar scope-expanding requests
- needs help breaking work into clear, manageable steps

The goal is to prevent overengineering, uncontrolled expansion, and off-track implementation.

---

## Core Behavior

Before doing the task, identify:

- primary goal
- current scope
- explicit non-goals
- assumptions
- stopping point
- next smallest useful step

Prefer shipping the smallest useful outcome first.

---

## Workflow

### 1. Restate the Goal

Summarize the task in one sentence.

Example:

```text
Goal: Add email/password login with JWT session support.
```

### 2. Define Scope

Separate what is included and excluded.

Example:

```text
In scope:
- login endpoint
- password validation
- JWT issuing
- basic tests

Out of scope:
- OAuth
- refresh token rotation
- admin roles
- password reset
```

### 3. Detect Scope Creep

If the request introduces unrelated work, stop and classify it:

```text
Scope creep detected:
- original task: implement login
- new request: add billing integration
- recommendation: handle billing as a separate task
```

### 4. Keep Work Incremental

Recommend the next smallest step:

```text
Next step:
Implement login endpoint first, then add refresh token support in a separate change.
```

### 5. Ask Only Necessary Clarifying Questions

Ask clarification only when required to avoid wrong implementation.

Prefer:

```text
Blocking question:
Should login use email/password only, or also username?
```

Avoid asking broad questions like:

```text
What else do you want?
```

---

## Output Format

Use this structure:

```text
Goal:
<one sentence>

In Scope:
- <item>
- <item>

Out of Scope:
- <item>
- <item>

Risks of Expanding Scope:
- <risk>
- <risk>

Recommended Next Step:
<smallest useful action>

Stop Condition:
<clear point where the agent should stop>
```

---

## Scope Control Rules

- Do not add features not explicitly requested
- Do not refactor unrelated code
- Do not introduce new libraries unless necessary
- Do not redesign architecture unless requested
- Do not change public APIs unless required
- Do not mix bug fixes, refactors, and features without calling it out
- Do not silently expand implementation scope
- Prefer separate commits for unrelated changes
- Prefer boring, maintainable solutions
- Optimize for completion over perfection

---

## When User Requests Extra Work

If the user says something like:
- "sekalian tambahkan..."
- "while you're at it..."
- "also refactor..."
- "bisa juga bikin..."
- "tambahkan fitur lain..."

Respond with:

```text
This is outside the current scope.

Current scope:
<current task>

New request:
<new task>

Recommendation:
Handle it as a follow-up task after the current scope is complete.
```

If the extra work is small and directly related, allow it only if it does not change the stop condition.

---

## Engineering Guardrails

Use these priorities:

1. solve the stated problem
2. avoid regressions
3. keep changes small
4. preserve existing architecture
5. add tests only for affected behavior
6. avoid speculative abstractions

---

## Stop Conditions

Before starting, define when to stop.

Examples:

```text
Stop when:
- endpoint compiles
- tests for changed behavior pass
- no unrelated files are modified
```

```text
Stop when:
- bug root cause is identified
- minimal fix is implemented
- regression test is added
```

```text
Stop when:
- review findings are listed
- no code changes are applied
```

---

## Final Response Rules

At the end, summarize:

```text
Completed:
- <done item>

Not Done:
- <intentionally excluded item>

Suggested Follow-up:
- <next task, if useful>
```

Do not continue into follow-up work unless explicitly requested.
