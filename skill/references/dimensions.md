# Dimension Details

Detailed checks for each of the 5 audit dimensions. Each table lists what to check, how to check it, and common drifts.

---

## 1. Docs ↔ Code

Are documentation files (README, CLAUDE.md, etc.) consistent with what the code actually does?

| What to check | How | Common drifts |
|---|---|---|
| CLI commands in docs | Compare documented commands vs actual CLI routing (e.g. `index.ts` switch/if chains) | Added command not documented, removed command still listed |
| Type names in docs | Compare type names mentioned in docs vs `types.ts` / `*.d.ts` | Renamed type, old name still in docs |
| File paths in docs | Grep doc-mentioned paths, verify they exist | Moved/renamed file, docs reference old path |
| Config options | Compare documented config keys vs actual config parsing code | New option undocumented, removed option still described |
| Architecture diagrams | Compare described flow vs actual import/call graph | New layer added, diagram outdated |

---

## 2. Plans ↔ Progress

Does the progress tracker accurately reflect what was planned?

| What to check | How | Common drifts |
|---|---|---|
| Completed items | Cross-ref progress [x] items with plan task list | Task marked done but plan has it as pending |
| Pending items | Verify pending items in progress match plan scope | Plan expanded, progress not updated |
| Phase boundaries | Check phase status labels match actual completion | Phase says "complete" but items still open |
| Deferred items | Verify deferred items are listed somewhere (progress or plan) | Silently dropped — not in progress, not in plan |
| Task descriptions | Confirm progress descriptions match plan intent | Scope changed during implementation, progress description stale |

---

## 3. Code ↔ Design

Does the implementation follow the design decisions documented in design docs?

| What to check | How | Common drifts |
|---|---|---|
| Architecture layers | Compare code import graph vs designed architecture | Layer bypass — code imports across boundary |
| Design decisions table | For each decision in design doc, verify code follows it | Decision made but code does opposite |
| Data flow | Compare designed signal/data flow vs actual flow | Added shortcut path not in design |
| Naming conventions | Check code names match design vocabulary | Design says "deck", code says "task" |
| Rejected alternatives | Verify code doesn't use explicitly rejected approaches | Rejected approach snuck in during implementation |

---

## 4. Skills ↔ Reality

Do skill files (SKILL.md, references, templates) match what the code can actually do?

| What to check | How | Common drifts |
|---|---|---|
| Commands in SKILL.md | Compare skill-documented commands vs actual CLI | Skill references command that doesn't exist |
| File paths in skills | Verify `.booth/` or other paths mentioned in skills | Path changed in code, skill references old path |
| Behavioral rules | Check if skill rules are enforceable by code | Skill says "always X" but code has no mechanism for it |
| Alert/signal types | Compare skill-documented types vs `types.ts` | New alert type in code, skill doesn't mention it |
| Template accuracy | Compare templates vs what code actually generates | Code output format changed, template outdated |

---

## 5. Progress ↔ Plans

Are next steps and future phases in progress still aligned with plans?

| What to check | How | Common drifts |
|---|---|---|
| Next phase scope | Compare progress's "not yet implemented" vs plan's next phase | Plan revised, progress still lists old scope |
| Priority ordering | Verify progress priorities match plan priorities | Plan re-prioritized, progress order stale |
| Dependencies | Check if progress respects plan's dependency ordering | Progress lists Phase 3 item as next, but Phase 2 dependency incomplete |
| Dropped items | Items in plan but missing from progress entirely | Forgot to add to progress tracker |
| New items | Items in progress not in any plan | Added ad-hoc, may need plan update |
