---
name: system-analyst
description: Analyze software systems, requirements, architecture, data flow, and technical constraints to produce structured engineering understanding and recommendations.
---

# System Analyst Skill

## Purpose

Analyze systems, requirements, architecture, and technical flows before implementation.

Use this skill whenever the user:
- asks for system design help
- asks for requirement analysis
- asks for architecture evaluation
- asks for data flow analysis
- asks how components should interact
- asks for backend/service modeling
- asks for event flow or transaction analysis

The goal is to produce:
- structured understanding
- system decomposition
- clear responsibilities
- technical constraints
- architectural recommendations
- implementation implications

---

# Analysis Workflow

## 1. Identify the Core Problem

Determine:
- business problem
- technical problem
- operational problem

Summarize in one sentence.

Example:

```text
Problem:
Ensure reliable cross-service order processing without distributed transactions.
```

---

## 2. Identify Actors

Determine:
- users
- systems
- services
- external providers
- scheduled jobs
- async workers

Example:

```text
Actors:
- customer
- auth service
- order service
- payment service
- Kafka broker
- shipping provider
```

---

## 3. Analyze Responsibilities

Define ownership clearly.

Example:

```text
Order Service:
- order lifecycle
- saga orchestration
- status transition

Payment Service:
- payment processing
- callback validation
- payment persistence
```

Avoid overlapping ownership.

---

## 4. Analyze Data Flow

Describe:
- request flow
- event flow
- async communication
- retries
- failure paths
- compensation flow

Example:

```text
Flow:
1. client creates order
2. order service emits order.created
3. payment service processes payment
4. payment.success event emitted
5. order status updated
```

---

## 5. Analyze State Transitions

Identify:
- lifecycle states
- valid transitions
- invalid transitions
- rollback/compensation

Example:

```text
Order States:
pending -> paid -> shipped -> completed

Invalid:
completed -> pending
```

---

## 6. Identify Constraints

Examples:
- latency
- consistency
- idempotency
- scalability
- compliance
- rate limits
- deployment limitations

---

## 7. Identify Risks

Examples:
- duplicate events
- stale cache
- race conditions
- partial failure
- inconsistent state
- retry storms

---

## 8. Evaluate Architecture

Review:
- service boundaries
- coupling
- scalability
- observability
- maintainability
- operational complexity

Prefer simple architecture unless complexity is justified.

---

# Output Format

Use this structure:

```text
Problem:
<problem>

Actors:
- <actor>

Responsibilities:
<component>:
- <responsibility>

System Flow:
1. <step>
2. <step>

State Transitions:
<state flow>

Constraints:
- <constraint>

Risks:
- <risk>

Architecture Notes:
- <note>

Recommendations:
- <recommendation>

Suggested Next Step:
- <next action>
```

---

# Analysis Rules

- Be explicit about assumptions
- Separate facts from recommendations
- Prefer clear ownership boundaries
- Avoid unnecessary abstractions
- Prefer operational simplicity
- Highlight consistency boundaries
- Call out hidden coupling
- Call out scalability bottlenecks
- Call out observability gaps
- Consider failure scenarios

---

# Distributed System Guidelines

For async/event-driven systems:
- identify idempotency requirements
- identify retry behavior
- identify ordering assumptions
- identify compensation strategy
- identify exactly-once assumptions
- identify timeout behavior

---

# API Analysis Guidelines

For APIs:
- analyze backward compatibility
- analyze pagination
- analyze auth flow
- analyze validation strategy
- analyze error contracts

---

# Database Analysis Guidelines

For DB-related systems:
- identify transaction boundaries
- identify locking risks
- identify migration risks
- identify indexing needs
- identify consistency tradeoffs

---

# Final Response Rules

Distinguish clearly between:
- current system understanding
- inferred assumptions
- recommendations
- optional improvements

Do not pretend certainty when information is incomplete.
