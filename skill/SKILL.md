---
name: self-review
description: Run a 5-dimension alignment audit on the current project. Use when the user says "self-review", "审视一下", or "audit". Report-only — never auto-fix.
---

# Self-Review — 5-Dimension Alignment Audit

A structured audit that checks whether a project's docs, code, plans, skills, and progress are in sync. Discovers anchors automatically, runs 5 checks, produces a report.

## Trigger

User says: `/self-review`, `审视一下`, `audit`, or `self-review`

## Process

### Step 1: Discover Anchors

Scan the project for these anchors (all optional — skip dimensions with no anchors):

| Anchor | Typical locations |
|--------|-------------------|
| Design docs | `CLAUDE.md`, `**/design/*.md`, `**/docs/*.md` |
| Progress | `**/progress.md`, `CHANGELOG.md` |
| Plans | `**/plan/*.md`, `**/plans/*.md` |
| Skills | `.claude/skills/`, `skill/SKILL.md`, `skill/references/` |
| Source code | `src/`, `lib/`, `app/` |
| Types | `**/types.ts`, `**/types.d.ts`, `**/models.ts` |

Report which anchors you found and which are missing.

### Step 2: Run 5 Dimensions

For each dimension, read the relevant anchors and check for drift. See `references/dimensions.md` for detailed checks per dimension.

1. **Docs ↔ Code** — Do docs match what the code actually does?
2. **Plans ↔ Progress** — Does progress reflect what plans said to do?
3. **Code ↔ Design** — Does implementation follow design decisions?
4. **Skills ↔ Reality** — Do skill files match actual code capabilities?
5. **Progress ↔ Plans** — Are next steps in progress still aligned with plans?

### Step 3: Report

Output a structured report in this format:

```
## Self-Review Report

### Anchors Found
- [list discovered anchors with paths]

### 1. Docs ↔ Code [✅ Aligned / ⚠️ Drift / ❌ Broken]
- [specific findings]

### 2. Plans ↔ Progress [✅ / ⚠️ / ❌]
- [specific findings]

### 3. Code ↔ Design [✅ / ⚠️ / ❌]
- [specific findings]

### 4. Skills ↔ Reality [✅ / ⚠️ / ❌]
- [specific findings]

### 5. Progress ↔ Plans [✅ / ⚠️ / ❌]
- [specific findings]

### Summary
- X/5 aligned, Y/5 drifted, Z/5 broken
- [top priority fixes, if any]
```

## Rules

- **Report only** — never auto-fix anything. Flag issues, don't resolve them.
- **Skip gracefully** — if an anchor doesn't exist, skip that dimension with a note.
- **Be specific** — cite file paths and line numbers, not vague descriptions.
- **No false positives** — only flag real drift, not stylistic differences.
- **Project-agnostic** — works on any project, not just booth.
