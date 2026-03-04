# Self-Review

An agent skill that runs structured alignment audits on any project. Checks whether your design, artifacts, skills, and progress are in sync. Works with Claude Code, Codex, OpenClaw, and any agent that supports the [AgentSkills](https://agentskills.io) standard.

## What It Does

Self-Review scans your project across **4 pillars** (Design, Artifact, Skill, Progress) and checks **7 dimensions** of alignment between them. It finds drift — where your docs say one thing but your code does another, where your progress claims completion but the artifact doesn't exist, where lessons learned haven't been captured.

**Report-only** — it flags issues, never auto-fixes.

Works for any project type: code, content, video, research — anything with deliverables.

## Install

### Claude Code

```bash
/plugin marketplace add motiful/self-review
/plugin install self-review@self-review-skills
```

### Codex

```bash
# In a Codex session:
$skill-installer install self-review from github.com/motiful/self-review
```

### OpenClaw

```bash
clawhub install self-review
```

### Manual (any agent)

```bash
git clone https://github.com/motiful/self-review.git
# Then symlink skill/ to your agent's skills directory:
ln -sfn "$(pwd)/self-review/skill" ~/.claude/skills/self-review      # Claude Code
ln -sfn "$(pwd)/self-review/skill" ~/.agents/skills/self-review      # Codex
ln -sfn "$(pwd)/self-review/skill" ~/.openclaw/skills/self-review    # OpenClaw
```

## Usage

Trigger the skill in any session:

- `/self-review` or `$self-review` (depending on platform)
- `self-review`
- `audit`

The skill scans your project, discovers anchors in each pillar, runs dimensional checks, and outputs a structured report with specific file paths and line numbers.

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

The skill automatically discovers project-level quality gates across platforms:

| Platform | Project instructions | Local overrides |
|----------|---------------------|-----------------|
| Claude Code | `CLAUDE.md` | `CLAUDE.local.md`, `.claude/rules/*.md` |
| Codex | `AGENTS.md` | `AGENTS.override.md` |
| OpenClaw | `AGENTS.md`, `SOUL.md` | via `openclaw.json` |
| Generic | `README.md`, `CONTRIBUTING.md` | linter configs |

These become additional checks in the deep dimensions.

## License

[MIT](LICENSE)
