---
name: self-review
description: Run a 4-pillar, 6-dimension alignment audit on the current project. Use when the user says "self-review", "审视一下", or "audit". Report-only — never auto-fix.
---

# Self-Review — 4-Pillar Alignment Audit

A structured audit that checks whether a project's design, artifacts, skills, and progress are in sync. Platform-agnostic, language-agnostic. Works for code, content, video, research — any project with deliverables.

## Trigger

User says: `/self-review`, `审视一下`, `audit`, or `self-review`

## The 4 Pillars

| Pillar | What it covers | Examples |
|--------|---------------|----------|
| **Design** | Intent, decisions, architecture, specs | CLAUDE.md, design docs, architecture diagrams, requirements, specs |
| **Artifact** | Actual deliverables — whatever was built | Code, articles, videos, reports, configs, skills, any output |
| **Skill** | How things are done — reusable methods, standards, accumulated know-how | SKILL.md, style guides, workflows, conventions, templates |
| **Progress** | Where we are — plans, tracking, milestones | progress.md, plans, changelogs, task lists, roadmaps |

Note: An artifact can itself be a skill (e.g. building a SKILL.md is both a deliverable and a methodology deposit).

## Process

### Step 1: Discover Anchors

Scan the project for anchors in each pillar (all optional — skip pillars with no anchors):

| Pillar | Typical anchors |
|--------|----------------|
| Design | `CLAUDE.md`, `**/design/*.md`, `**/docs/*.md`, `README.md` |
| Artifact | `src/`, `lib/`, `app/`, `dist/`, `output/`, `**/types.ts` |
| Skill | `.claude/skills/`, `skill/`, `**/references/*.md`, `**/templates/` |
| Progress | `**/progress.md`, `**/plan/*.md`, `CHANGELOG.md`, `**/roadmap.md` |

Report which anchors you found and which pillars have none.

### Step 2: Run 6 Dimensions

Each dimension checks drift between two pillars. Progress-adjacent dimensions (1-3) are highest priority — always run these. Design/Artifact/Skill cross-checks (4-6) run in deep audits or when specifically relevant.

See `references/dimensions.md` for detailed checks per dimension.

**Priority (Progress-centric):**
1. **Progress ↔ Design** — Are we aligned with design intent?
2. **Progress ↔ Artifact** — Does claimed status match actual deliverables?
3. **Progress ↔ Skill** — Any lessons to capture? Existing skills need updating?

**Deep audit:**
4. **Design ↔ Artifact** — Does the output match the design?
5. **Design ↔ Skill** — Do our methods support our design goals?
6. **Artifact ↔ Skill** — Does the output follow established methods?

### Step 3: Report

Output a structured report:

```
## Self-Review Report

### Anchors Found
- **Design**: [paths]
- **Artifact**: [paths]
- **Skill**: [paths]
- **Progress**: [paths]

### Priority Dimensions (Progress-centric)

#### 1. Progress ↔ Design [✅ Aligned / ⚠️ Drift / ❌ Broken]
- [specific findings with file paths]

#### 2. Progress ↔ Artifact [✅ / ⚠️ / ❌]
- [specific findings]

#### 3. Progress ↔ Skill [✅ / ⚠️ / ❌]
- [specific findings]

### Deep Dimensions

#### 4. Design ↔ Artifact [✅ / ⚠️ / ❌]
- [specific findings]

#### 5. Design ↔ Skill [✅ / ⚠️ / ❌]
- [specific findings]

#### 6. Artifact ↔ Skill [✅ / ⚠️ / ❌]
- [specific findings]

### Summary
- X/6 aligned, Y/6 drifted, Z/6 broken
- [top priority fixes, if any]
- [skill deposit candidates with recommendation: deposit / don't deposit / revisit when]
```

## Rules

- **Report only** — flag issues, never auto-fix.
- **Progress first** — always start from "what are we doing now?" and radiate outward.
- **Skip gracefully** — if a pillar has no anchors, skip its dimensions with a note.
- **Be specific** — cite file paths and line numbers, not vague descriptions.
- **No false positives** — only flag real drift, not stylistic differences.
- **Skill deposits need criteria** — always check for lessons to capture, but evaluate each candidate against the deposit criteria in `references/dimensions.md` (Dimension 3). Not every solved problem is worth a skill file.
- **Platform-agnostic** — works for code, content, video, research, anything.
- **Language-agnostic** — no assumption about programming language or human language.
