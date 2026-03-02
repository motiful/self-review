---
name: self-review
description: Run a 4-pillar alignment audit on the current project. Use when the user says "self-review", "审视一下", or "audit". Report-only — never auto-fix.
---

# Self-Review — 4-Pillar Alignment Audit

A structured audit that checks whether a project's design, artifacts, methodology, and progress are in sync. Platform-agnostic, language-agnostic. Works for code, content, video, research — any project with deliverables.

## Trigger

User says: `/self-review`, `审视一下`, `audit`, or `self-review`

## The 4 Pillars

| Pillar | What it covers | Examples |
|--------|---------------|----------|
| **Design** | Intent, decisions, architecture, specs | CLAUDE.md, design docs, architecture diagrams, requirements |
| **Artifact** | Actual deliverables — whatever was built | Code, articles, videos, reports, configs, any output |
| **Methodology** | How things are done — processes, standards, skills | SKILL.md, style guides, workflows, conventions, linting rules |
| **Progress** | Where we are — plans, tracking, milestones | progress.md, plans, changelogs, task lists, roadmaps |

## Process

### Step 1: Discover Anchors

Scan the project for anchors in each pillar (all optional — skip pillars with no anchors):

| Pillar | Typical anchors |
|--------|----------------|
| Design | `CLAUDE.md`, `**/design/*.md`, `**/docs/*.md`, `README.md` |
| Artifact | `src/`, `lib/`, `app/`, `dist/`, `output/`, `**/types.ts` |
| Methodology | `.claude/skills/`, `skill/`, `**/references/*.md`, `**/templates/` |
| Progress | `**/progress.md`, `**/plan/*.md`, `CHANGELOG.md`, `**/roadmap.md` |

Report which anchors you found and which pillars have none.

### Step 2: Run 4 Dimensions

Each dimension checks drift between two pillars. See `references/dimensions.md` for detailed checks.

1. **Design ↔ Artifact** — Does the output match the design?
2. **Methodology ↔ Artifact** — Does the output follow the established methods?
3. **Design ↔ Progress** — Are plans and trajectory aligned with design intent?
4. **Progress ↔ Artifact** — Does claimed status match actual deliverables?

### Step 3: Report

Output a structured report:

```
## Self-Review Report

### Anchors Found
- **Design**: [paths]
- **Artifact**: [paths]
- **Methodology**: [paths]
- **Progress**: [paths]

### 1. Design ↔ Artifact [✅ Aligned / ⚠️ Drift / ❌ Broken]
- [specific findings with file paths]

### 2. Methodology ↔ Artifact [✅ / ⚠️ / ❌]
- [specific findings]

### 3. Design ↔ Progress [✅ / ⚠️ / ❌]
- [specific findings]

### 4. Progress ↔ Artifact [✅ / ⚠️ / ❌]
- [specific findings]

### Summary
- X/4 aligned, Y/4 drifted, Z/4 broken
- [top priority fixes, if any]
```

## Rules

- **Report only** — flag issues, never auto-fix.
- **Skip gracefully** — if a pillar has no anchors, skip its dimensions with a note.
- **Be specific** — cite file paths and line numbers, not vague descriptions.
- **No false positives** — only flag real drift, not stylistic differences.
- **Platform-agnostic** — works for code, content, video, research, anything.
- **Language-agnostic** — no assumption about programming language or human language.
