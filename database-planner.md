---
name: database-planner
description: Design database schema, relationships, migrations, indexing, and consistency strategy for scalable applications.
---

# Database Planner Skill

## Purpose

Plan safe and scalable database structures.

Focus on:
- schema design
- normalization
- indexing
- migration safety
- transaction boundaries
- consistency

---

# Workflow

1. Analyze entities
2. Define relationships
3. Define ownership
4. Design indexes
5. Evaluate migration safety
6. Evaluate scalability

---

# Output Format

```text
Entities:
- <entity>

Relationships:
- <relationship>

Indexes:
- <index>

Migration Plan:
1. <step>

Risks:
- <risk>

Recommendations:
- <recommendation>
```

---

# Rules

- prefer explicit constraints
- avoid over-normalization
- avoid premature sharding
- prioritize migration safety
- consider rollback strategy
