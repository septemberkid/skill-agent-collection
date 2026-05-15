---
name: git-commit
description: Recommend accurate Conventional Commit messages by analyzing git diff, staged changes, and repository modifications.
---

# Git Commit Message Skill

## Purpose

Analyze git changes and recommend high-quality commit messages based on the actual code modifications.

Use this skill whenever the user:
- asks for commit message recommendations
- asks to summarize git changes
- asks to generate Conventional Commit messages
- asks whether changes should be split into multiple commits

## Workflow

### 1. Inspect Repository State

Run:

```bash
git status --short
git diff --stat
git diff
```

If staged changes exist, also run:

```bash
git diff --staged
```

### 2. Understand Change Intent

Inspect the diff carefully and determine:

- affected module or domain
- behavioral change
- bug fix vs refactor vs feature
- config/tooling/dependency updates
- test additions or updates
- documentation-only changes

Do not invent business context that is not visible in the diff.

### 3. Classify Commit Type

Use Conventional Commits:

| Type | Usage |
|---|---|
| feat | new functionality |
| fix | bug fix |
| refactor | restructuring without behavior change |
| perf | performance optimization |
| test | test-only changes |
| docs | documentation changes |
| style | formatting/lint-only |
| chore | maintenance/config/tooling |
| build | build system/dependency updates |
| ci | CI/CD updates |

### 4. Determine Scope

Prefer concise scopes:

Examples:
- auth
- payment
- order
- inventory
- api
- db
- deps
- config

If no clear scope exists, omit the scope.

Examples:

```text
feat(auth): add refresh token rotation
fix(order): prevent duplicate checkout request
refactor(api): simplify request validation
chore(deps): update hono and zod versions
```

### 5. Detect Mixed Changes

If unrelated changes are detected, recommend splitting commits.

Example:

```text
This diff should be split into multiple commits:

1. feat(auth): add session refresh endpoint
2. test(auth): add coverage for expired token flow
3. chore(config): update eslint configuration
```

## Output Format

Use this structure:

```text
Recommended commit message:
<message>

Why:
- <reason>
- <reason>

Alternatives:
1. <alternative>
2. <alternative>
3. <alternative>
```

## Rules

- Keep summary concise
- Prefer under 72 characters
- Use imperative mood
- Use lowercase commit type
- Only describe what actually changed
- Avoid vague summaries like:
  - update code
  - fix stuff
  - improve system

Prefer explicit descriptions:
- fix(auth): validate expired jwt token
- feat(payment): add xendit callback handler

## Special Cases

### Staged and Unstaged Changes

If both exist:

- generate recommendation for staged changes
- generate separate recommendation for unstaged changes

### Large Diffs

If diff is too large:

- summarize by logical areas
- recommend multiple commits if necessary

### Unclear Changes

If intent is unclear:

- explain uncertainty
- provide safest generic commit recommendation

Example:

```text
chore: update internal implementation
```
