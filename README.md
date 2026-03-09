# Self-Review

> Structured reflection for any creative work — code, content, design, research.

[Agent Skills](https://agentskills.io) compatible — works with Claude Code, Cursor, Codex, OpenClaw, and any supporting platform.

## Who Is This For

Anyone producing work with intent.

- **Developers**: Are you building what you designed? Does the code match the spec?
- **Content creators**: Does the final cut match the script? Did you capture your editing lessons?
- **Designers**: Does the mockup address the user need? Is there a simpler layout?
- **Researchers**: Do the conclusions follow from the method? Is the progress tracking accurate?
- **Teams**: Are design, delivery, and documentation in sync across contributors?

You don't need formal documents to use Self-Review. If your "design" is a mental model and your "progress" is a git log — that's enough. The 4 pillars are questions to ask, not documents to write.

## Why This Exists

Anyone who ships work in stages faces the same problem: things drift.

The design says one thing, the deliverable does another. Progress tracking says "done" but the artifact is half-finished. You learned a better method last week but the old pattern is still everywhere.

Self-Review forces a structured pause. It scans your project across **4 pillars** and checks **6 dimensions** of alignment between them. It works for anything with deliverables — code, content, research, design.

It's especially powerful as an AI agent skill — agents are goal-seeking and don't naturally pause to reflect. But the framework works for any creator reviewing their own work.

**Report-only** — it flags issues, never auto-fixes. You stay in control.

## Why These Principles

The 6 audit principles draw from two sources:

**Feynman's criteria for good theories** (The Character of Physical Law, 1964):
1. It must agree with experiment → **Verifiable & Verified**
2. It must be self-consistent → **No Internal Contradiction**
3. It must be the simplest explanation → **Simplest Sufficient Solution**

**Engineering constraints** that theory alone doesn't cover:
4. It must be buildable → **Feasible**
5. It must handle edge cases → **Boundary-Complete**
6. It must be handoff-ready → **Maintainable**

The theoretical layer tells you "is this a good idea?". The engineering layer tells you "can this actually ship?". Self-Review checks both.

## The 4 Pillars

Pillars are lenses for examining the same body of work — not file categories.

| Pillar | Core question | What it covers |
|--------|--------------|----------------|
| **Design** | Why are we doing this? What should it become? | Intent, decisions, constraints, specs |
| **Artifact** | What was actually produced? | Any deliverable — code, documents, designs, videos, skills, configs |
| **Skill** | How do we do things? What did we learn? | Reusable methods, standards, accumulated know-how |
| **Progress** | Where are we? What's next? | Plans, status, milestones, tracking |

The same deliverable can be examined through multiple pillars. A design doc is both Design (intent) and Artifact (deliverable). A pillar may have no dedicated files — intent might live only in commit messages, progress only in branch status.

## The 6 Dimensions

Checks alignment between every pillar pair — the complete C(4,2) combination with no exceptions.

**Priority (always run):**
1. **Progress <> Design** — Are we aligned with design intent?
2. **Progress <> Artifact** — Does claimed status match actual deliverables?
3. **Progress <> Skill** — Any lessons to capture?

**Deep audit:**
4. **Design <> Artifact** — Does the output match the design?
5. **Design <> Skill** — Do our methods support our design goals?
6. **Artifact <> Skill** — Does the output follow established methods?

## What Makes It Different

**Scope-aware auditing.** Before checking anything, Self-Review reads your Progress to lock the current phase. It classifies items as in-scope, deferred, or out-of-scope — then only audits in-scope work. "Phase 2 hasn't started yet" is never a finding.

**It actually runs your code.** Dimension 2 doesn't just check if files exist — it executes builds, runs CLI commands, and verifies output at integration level. "Tests pass" means it ran the tests.

**Design introspection with research.** Before checking cross-pillar alignment, it evaluates the design itself: Is this a well-defined problem? Are there blind spots or stale assumptions? Is this the simplest sufficient solution? It actively searches the web to verify assumptions against the latest information.

**Principled judgment.** Every finding is evaluated against 6 explicit principles (3 theoretical + 3 engineering), embedded as check questions directly in each dimension. This makes audits consistent and reviewable.

**Personalized quality standards.** Each project gets its own review rules. Self-Review discovers your project's instruction files (`CLAUDE.md`, `AGENTS.md`, `.cursorrules`) and domain skills, then uses them as additional quality gates. When it finds recurring issues with no corresponding standard, it recommends exactly which file to add the standard to and drafts the content.

**Skill deposit detection.** Dimension 3 doesn't just check alignment — it evaluates whether lessons learned during execution are worth capturing as reusable skills. It applies specific deposit criteria (cross-project reusable? counter-intuitive trap? right granularity?) so you don't waste time formalizing patterns that aren't worth it.

**Works for everything.** Not just code. Content projects, research, video production, documentation — anything with a design intent and deliverables.

## Install

```bash
npx skills add motiful/self-review
```

Or manually:

```bash
git clone https://github.com/motiful/self-review ~/skills/self-review
# Then symlink skill/ to your agent's skills directory
# Claude Code: ln -sfn ~/skills/self-review/skill ~/.claude/skills/self-review
# Cursor:      ln -sfn ~/skills/self-review/skill ~/.cursor/skills/self-review
# Codex:       ln -sfn ~/skills/self-review/skill ~/.agents/skills/self-review
```

## Usage

Say: `/self-review`, `self-review`, `audit`, or `审视一下`

The skill scans your project, discovers anchors in each pillar, locks the current scope from Progress, runs dimensional checks, and outputs a structured report with specific file paths and line numbers.

## Example Output

### Example: Self-Review Auditing Itself (Real Output)

```
## Self-Review Report

### Design Introspection
- Clarity: well-defined — "4-pillar, 6-dimension alignment audit"
- Scope: appropriate, focused on audit methodology
- Simplicity: principles condensed to 6-row index table, details inline in dimensions

### Scope Lock
- Current phase: Content refactoring (pillar redefinition, principle inlining, cross-domain support)
- In-scope: SKILL.md, dimensions.md, README.md
- Deferred: none (single-phase refactor)

### Anchors Found
- Design: README.md, refactoring plan (conversation context)
- Artifact: skill/SKILL.md, skill/references/dimensions.md
- Skill: skill/ directory (self-review is itself a skill)
- Progress: [inferred] git diff — 3 files changed, 358 insertions, 135 deletions

### Priority Dimensions

#### 1. Progress <> Design [Aligned]
- All planned changes implemented, "do not change" items preserved

#### 2. Progress <> Artifact [Drift]
- .claude-plugin/plugin.json still says "7-dimension" (should be "6-dimension")
- .claude-plugin/marketplace.json has same stale description
- README line 31: "three sources" should be "two sources"

#### 3. Progress <> Skill [Aligned]
- No new skill deposit needed — this is a refactor of existing skill

### Summary
- 4/6 aligned, 2/6 drifted, 0/6 broken
- Top fix: delete stale .claude-plugin/ directory, fix "three sources" typo
```

### Example: Video Project (Hypothetical)

```
## Self-Review Report

### Scope Lock
- Current phase: Episode 3 rough cut
- In-scope: filming, rough edit, audio sync
- Deferred: color grading, final mix (post-production phase)

### Priority Dimensions

#### 1. Progress <> Design [Drift]
- Script calls for 5 scenes, only 4 filmed. Scene 3 (interview) not scheduled.

#### 2. Progress <> Artifact [Aligned]
- Rough cut exists, 12:34 duration (target: 12-15 min)
- Audio synced, no dropout detected
- L2 verified: playable, continuity intact

#### 3. Progress <> Skill [Aligned]
- Editing pattern: consistent use of J-cuts per team style guide

### Summary
- 5/6 aligned, 1/6 drifted, 0/6 broken
```

## What's Inside

```
skill/
├── SKILL.md              — Audit process, principles, and rules
└── references/
    └── dimensions.md     — Detailed checks for all 6 dimensions
```

## License

[MIT](LICENSE)
