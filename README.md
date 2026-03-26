<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/logo-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset=".github/logo-light.svg">
    <img alt="self-review" src=".github/logo-light.svg" width="440">
  </picture>
</div>

> Catch drift between design and delivery before it ships.

<div align="center">

[Agent Skills](https://agentskills.io) compatible — works with Claude Code, Cursor, Codex, OpenClaw, and any supporting platform.

[![License: MIT][license-shield]][license-url]

[Usage](#usage) · [Install](#install) · [Example Output](#example-output)

</div>

## Who Is This For

Anyone producing work with intent.

- **Developers**: Are you building what you designed? Does the code match the spec?
- **Content creators**: Does the final cut match the script? Did you capture your editing lessons?
- **Designers**: Does the mockup address the user need? Is there a simpler layout?
- **Researchers**: Do the conclusions follow from the method? Is the progress tracking accurate?
- **Teams**: Are design, delivery, and documentation in sync across contributors?

You don't need formal documents to use Self-Review. If your "design" is a mental model and your "progress" is a git log — that's enough. The 4 pillars are questions to ask, not documents to write.

**Not for**: line-by-line code review, automated CI gates, or linting. Self-Review checks alignment between intent and delivery — it does not evaluate code style, syntax, or formatting.

## Why This Exists

Anyone who ships work in stages faces the same problem: things drift.

The design says one thing, the deliverable does another. Progress tracking says "done" but the artifact is half-finished. You learned a better method last week but the old pattern is still everywhere.

Self-Review forces a structured pause. It scans your project across **4 pillars** and checks **6 dimensions** of alignment between them. It works for anything with deliverables — code, content, research, design.

It's especially powerful as an AI agent skill — agents are goal-seeking and don't naturally pause to reflect. But the framework works for any creator reviewing their own work.

**Report-only** — it flags issues, never auto-fixes. You stay in control.

## What Makes It Different

**Scope-aware auditing.** Self-Review reads your Progress to lock the current phase before checking anything. Items are classified as in-scope, deferred, or out-of-scope — only in-scope work gets audited. "Phase 2 hasn't started yet" is never a finding.

**Artifact verification, not just existence checks.** The artifact check runs your builds, executes CLI commands, and verifies output — not just that files exist, but that they actually work. "Tests pass" means it ran the tests.

**Design introspection.** Evaluates your design for clarity, value, scope, and simplicity before checking alignment. Asks whether the goal is well-defined, the scope is right-sized, and whether a simpler approach exists.

**Currency and assumptions check.** Searches the web with current-year queries to verify your design assumptions still hold. Flags when a key assumption has been invalidated or when a community solution has dissolved the problem you're solving custom.

**Principled judgment.** Every finding is evaluated against 6 explicit principles (3 theoretical + 3 engineering), embedded as check questions directly in each dimension. Audits are consistent and reviewable.

**Cross-platform quality standards.** Discovers your project's instruction files across platforms — `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, `.cursor/rules/`, `CONTRIBUTING.md` — and uses them as additional quality gates. Also layers rules from installed domain skills.

**Standard recommendations.** When recurring issues have no corresponding standard, Self-Review drafts the standard text, specifies the exact file path where it should be persisted (platform-aware), and explains why it's worth adding.

**Implicit anchor inference.** No dedicated design docs? No progress.md? Infers from commit messages, PR descriptions, TODO comments, git log timelines, and code patterns before skipping any pillar.

**Skill deposit detection.** Evaluates whether lessons learned during execution are worth capturing as reusable skills, with specific deposit criteria and clear recommendations.

**Works for everything.** Code, content, research, video production, documentation — anything with a design intent and deliverables.

## Usage

Say `/self-review`, `self-review`, `audit`, or `审视一下`.

Self-Review discovers anchors in 4 pillars, locks scope, runs all 6 dimensions with artifact verification (minimum level depends on artifact type), and outputs a structured report with file paths and line numbers.

## Install

```bash
npx skills add motiful/self-review
```

Or manually:

```bash
git clone https://github.com/motiful/self-review ~/skills/self-review

# Claude Code
ln -sfn ~/skills/self-review ~/.claude/skills/self-review

# Other platforms (Cursor, Codex, Windsurf, etc.)
ln -sfn ~/skills/self-review ~/.agents/skills/self-review
```

## Example Output

Self-Review produces a structured report covering design introspection, scope lock, and all 6 dimensional checks with specific findings and evidence.

→ [Full examples](docs/examples.md) — includes a real self-audit and a hypothetical video project audit

## The Framework

Self-Review is built on 6 audit principles (3 from Feynman's criteria for good theories + 3 engineering constraints), applied across 4 pillars (Design, Artifact, Skill, Progress) in all 6 pillar-pair dimensions.

→ [Principles, pillars, dimensions, and verification depth](docs/framework.md)

## What's Inside

```
SKILL.md              — Audit process, execution procedure, and rules
references/
└── dimensions.md     — Detailed checks for all 6 dimensions
docs/
├── examples.md       — Sample audit outputs
└── framework.md      — Principles, pillars, and dimensions explained
```

## Contributing

Issues, suggestions, and PRs welcome at [github.com/motiful/self-review](https://github.com/motiful/self-review).

## License

[MIT](LICENSE)

---

Forged with [Skill Forge](https://github.com/motiful/skill-forge) · Crafted with [Readme Craft](https://github.com/motiful/readme-craft)

[license-shield]: https://img.shields.io/github/license/motiful/self-review.svg
[license-url]: https://github.com/motiful/self-review/blob/main/LICENSE
