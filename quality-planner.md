---
name: quality-planner
description: Plan quality gates, validation strategy, testing scope, risk checks, and acceptance criteria before implementing or releasing software changes.
---

# Quality Planner Skill

## Purpose

Create a practical quality plan for engineering work before implementation, review, or release.

Use this skill whenever the user:
- asks for quality planning
- wants validation strategy
- wants acceptance criteria
- wants test scope
- wants release readiness checks
- wants risk-based QA planning
- wants to avoid regressions before shipping

The goal is to define:
- what must be validated
- how it should be validated
- which risks matter most
- what is acceptable to ship
- what should block release

---

# Core Principles

Prioritize:

1. correctness
2. user-impacting behavior
3. regression prevention
4. data consistency
5. security
6. reliability
7. observability
8. maintainability

Avoid:
- testing everything blindly
- excessive manual QA
- vague acceptance criteria
- release blockers without clear reason
- low-value test cases

---

# Workflow

## 1. Understand the Change

Identify:

- goal of the change
- affected modules
- affected users
- affected APIs
- affected data
- affected integrations
- runtime or deployment impact

---

## 2. Identify Quality Risks

Classify risks by area:

- correctness
- regression
- security
- performance
- data consistency
- backward compatibility
- migration safety
- observability
- operational failure

Example:

```text
Risk:
Payment callback may be processed more than once.
Impact:
Duplicate order status updates or inconsistent payment state.
```

---

## 3. Define Quality Gates

Quality gates are checks that must pass before the task is considered done.

Examples:

```text
Quality Gates:
- changed unit tests pass
- integration tests pass for payment callback flow
- migration is backward compatible
- no public API contract regression
- structured logs include correlation id
```

---

## 4. Define Test Strategy

Break testing into:

### Unit Tests
Validate isolated business logic.

### Integration Tests
Validate module/service/database boundaries.

### Contract Tests
Validate API/event payload compatibility.

### Regression Tests
Validate previously broken or risky behavior.

### Manual Checks
Validate UX, operational behavior, or flows hard to automate.

---

## 5. Define Acceptance Criteria

Acceptance criteria must be observable and testable.

Good:

```text
- user cannot create order when inventory reservation fails
- payment callback is idempotent for duplicate provider events
- failed payment transitions order to payment_failed
```

Bad:

```text
- payment flow works well
- system is stable
```

---

## 6. Define Release Readiness

Check:

- config/env changes
- migrations
- feature flags
- rollback plan
- monitoring/logging
- backward compatibility
- known limitations

---

# Output Format

Use this structure:

```text
Quality Plan

Goal:
<goal>

Risk Areas:
1. <risk>
- Impact:
- Validation:

Quality Gates:
- <gate>

Test Strategy:
Unit:
- <test>

Integration:
- <test>

Contract:
- <test>

Regression:
- <test>

Manual Checks:
- <check>

Acceptance Criteria:
- <criteria>

Release Readiness:
- <check>

Blockers:
- <blocker>

Non-Goals:
- <excluded validation>
```

---

# Risk Severity

Use:

| Severity | Meaning |
|---|---|
| critical | can cause data loss, security issue, or major outage |
| high | can break core user flow or production behavior |
| medium | can cause degraded UX, reliability, or maintainability |
| low | minor issue or cleanup |

---

# Planning Rules

- Prefer risk-based validation
- Keep checks proportional to change size
- Prioritize automated tests over manual checks
- Include manual QA only when automation is impractical
- Call out release blockers clearly
- Do not require excessive gates for low-risk changes
- Separate must-have checks from nice-to-have checks
- Avoid vague quality criteria

---

# Special Cases

## Database Changes

Include checks for:

- migration safety
- rollback safety
- nullable/default strategy
- index impact
- lock risk
- backward compatibility

---

## API Changes

Include checks for:

- request validation
- response compatibility
- error contract
- auth behavior
- pagination/filtering if relevant

---

## Event-Driven Systems

Include checks for:

- idempotency
- retry behavior
- ordering assumptions
- duplicate event handling
- dead-letter behavior
- correlation id propagation

---

## Authentication or Authorization

Include checks for:

- unauthorized access
- privilege escalation
- token/session handling
- missing ownership validation
- audit logging

---

## Frontend Changes

Include checks for:

- loading state
- empty state
- error state
- accessibility basics
- form validation
- state persistence
- API failure handling

---

# Final Response Rules

At the end, summarize:

```text
Must Pass:
- <required gate>

Should Check:
- <recommended check>

Can Defer:
- <non-blocking check>
```

Do not expand into implementation unless explicitly requested.
