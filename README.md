# Self-Review

A Claude Code skill that runs structured alignment audits on any project. Checks whether your design, artifacts, skills, and progress are in sync.

## What It Does

Self-Review scans your project across **4 pillars** (Design, Artifact, Skill, Progress) and checks **7 dimensions** of alignment between them. It finds drift — where your docs say one thing but your code does another, where your progress claims completion but the artifact doesn't exist, where lessons learned haven't been captured.

**Report-only** — it flags issues, never auto-fixes.

Works for any project type: code, content, video, research — anything with deliverables.

## Install

Clone and symlink to your Claude Code skills directory:

```bash
git clone https://github.com/motiful/self-review.git
ln -sfn "$(pwd)/self-review/skill" ~/.claude/skills/self-review
```

## Usage

In any Claude Code session, say:

- `/self-review`
- `self-review`
- `audit`

The skill will scan your project, discover anchors in each pillar, run dimensional checks, and output a structured report with specific file paths and line numbers.

## The 4 Pillars

| Pillar | What it covers |
|--------|---------------|
| **Design** | Intent, decisions, architecture, specs |
| **Artifact** | Actual deliverables — whatever was built |
| **Skill** | Reusable methods, standards, accumulated know-how |
| **Progress** | Plans, tracking, milestones |

## The 7 Dimensions

**Priority (always run):**
1. Progress ↔ Design — Are we aligned with design intent?
2. Progress ↔ Artifact — Does claimed status match actual deliverables?
3. Progress ↔ Skill — Any lessons to capture?

**Deep audit:**
4. Design ↔ Artifact — Does the output match the design?
5. Design ↔ Skill — Do our methods support our design goals?
6. Artifact ↔ Skill — Does the output follow established methods?
7. Documentation Completeness — Are all significant changes documented?

## Example Output

```
## Self-Review Report

### Anchors Found
- Design: CLAUDE.md, docs/architecture.md
- Artifact: src/, dist/
- Skill: skill/SKILL.md
- Progress: .claude/progress.md

### Priority Dimensions

#### 1. Progress ↔ Design [⚠️ Drift]
- progress.md says Phase 2 complete, but design doc still references removed API

#### 2. Progress ↔ Artifact [✅ Aligned]
- All claimed deliverables verified in code

### Summary
- 5/7 aligned, 2/7 drifted, 0/7 broken
```

## Project-Specific Standards

The skill automatically discovers project-level quality gates:

- `CLAUDE.md` — project principles and conventions
- `CLAUDE.local.md` — local development rules
- `.claude/rules/*.md` — automated quality standards

These become additional checks in the deep dimensions.

## License

[MIT](LICENSE)
