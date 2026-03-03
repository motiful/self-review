# Dimension Details

Detailed checks for all 6 audit dimensions. Dimensions 1-3 are Progress-centric (highest priority). Dimensions 4-6 are cross-pillar deep checks.

---

## Priority Dimensions (Progress-centric)

### 1. Progress ↔ Design

Are we aligned with design intent?

| What to check | How | Common drifts |
|---|---|---|
| Phase alignment | Compare progress phase status vs design milestones | Progress says "Phase 2 done", design goals not met |
| Priority ordering | Verify progress priorities match design priorities | Design says A before B, progress has B first |
| Scope consistency | Compare planned scope in progress vs design scope | Design expanded, progress still lists old scope |
| Direction check | Is the trajectory moving toward the design vision? | Progress shows activity, but drifting from design goals |
| Deferred items | Verify deferred items are tracked somewhere | Silently dropped — not in progress, not in design |
| Dependency ordering | Check progress respects design's dependency chain | Phase 3 item started, but Phase 2 dependency unfinished |

### 2. Progress ↔ Artifact

Does claimed status match actual deliverables?

| What to check | How | Common drifts |
|---|---|---|
| Completion claims | Cross-ref "done" items in progress vs actual artifacts | Marked done but artifact incomplete or missing |
| Pending accuracy | Verify "pending" items are actually unstarted | Work started but progress not updated |
| Artifact inventory | Check for artifacts not reflected in progress | Built something, forgot to track it |
| Status freshness | Compare artifact timestamps vs progress update timestamps | Artifact changed after last progress update |
| Deliverable evidence | For each claimed deliverable, verify it exists and works | Progress claims "tests pass" but tests don't exist |
| Gap detection | Items in progress with no corresponding artifact | Planned but never started, or started and abandoned |

### 3. Progress ↔ Skill

Any lessons to capture? Existing skills need updating?

| What to check | How | Common drifts |
|---|---|---|
| New skill opportunities | Review completed work for reusable patterns worth capturing | Solved a hard problem, didn't deposit the knowledge |
| Skill staleness | Check if existing skills still match current practices | Skill says "do X", but we've since learned "do Y" |
| Process compliance | Did execution follow documented skills/methods? | Skill says "always review", no review evidence |
| Conflict detection | Do recent learnings contradict existing skills? | New finding invalidates old skill rule |
| Skill coverage gaps | Are there active areas with no corresponding skill? | Doing complex work repeatedly with no documented method |
| Deposit backlog | List skills that should exist but don't yet | Pattern used 3+ times but never formalized |

#### Skill Deposit Criteria

When this dimension flags potential skill deposits, evaluate each candidate against these criteria. A pattern is worth depositing when it meets **at least one** of:

1. **Cross-project reusable** — The pattern applies across 3+ different projects. Deposit as a global skill.
2. **User-facing in a skills project** — The project itself IS a skills/tools project. Patterns that capture user intent, trigger timing, or solve user-facing interaction problems are worth depositing because users will hit these same issues.
3. **Intra-project SOP** — Even within a single project, if the pattern forms a repeatable workflow (editing technique, debugging SOP, review checklist) that you'll use again and again, it's worth depositing.

**NOT worth depositing:**

- **Code is the documentation** — If the pattern is already well-expressed in code + inline comments, extracting it adds maintenance burden with no value. Code IS the best documentation for implementation patterns.
- **Pure annotations** — Comments-level insights don't need separate files.
- **Wrong granularity** — Too fine (no application scenario, e.g. "always use setTimeout not setInterval for one-shot delays") or too coarse (covers everything, e.g. "write good code"). Right granularity: someone encountering the same class of problem would benefit from reading this before starting.
- **No counter-intuitive trap** — If the "obvious" approach works fine, there's nothing to deposit. Skills capture the non-obvious.

#### How to Report Skill Deposit Candidates

For each candidate pattern flagged by this dimension:

1. State the pattern briefly
2. Evaluate against the criteria above — which conditions does it meet?
3. Give a clear recommendation: **deposit** / **don't deposit** / **revisit when [condition]**
4. If "don't deposit": explain why (usually "code is the doc" or "not reusable enough")

---

## Deep Dimensions

### 4. Design ↔ Artifact

Does what was built match what was designed?

| What to check | How | Common drifts |
|---|---|---|
| Spec vs output | Compare design specs/requirements against actual deliverables | Feature designed but not built, or built differently |
| Architecture adherence | Compare designed structure vs actual structure | Layer bypass, unauthorized dependency |
| Naming consistency | Check artifact names match design vocabulary | Design says "deck", artifact says "task" |
| Decision compliance | For each recorded decision, verify artifact follows it | Decision made but artifact does the opposite |
| Rejected alternatives | Verify artifact doesn't use explicitly rejected approaches | Rejected approach snuck in during execution |
| Scope boundaries | Compare designed scope vs what artifact actually covers | Scope creep or under-delivery |

### 5. Design ↔ Skill

Do our methods support our design goals?

| What to check | How | Common drifts |
|---|---|---|
| Principle-method alignment | For each design principle, check if a supporting skill exists | Design says "test-driven" but no testing skill |
| Constraint enforcement | Are design constraints backed by enforceable methods? | Design says "no direct DB access" but no skill enforces it |
| Vocabulary alignment | Do skills use the same terms as design docs? | Design says "artifact", skill says "deliverable" |
| Coverage | Are all critical design areas supported by skills? | Design has 5 pillars, skills only cover 2 |
| Anti-pattern prevention | Do skills guard against design's rejected alternatives? | Design rejected approach X, no skill warns against it |

### 6. Artifact ↔ Skill

Does the output follow established methods?

| What to check | How | Common drifts |
|---|---|---|
| Standards adherence | Check artifact against documented standards | Standard exists but artifact violates it |
| Template conformance | Compare templates vs what artifact actually produces | Template updated, artifact still uses old format |
| Skill accuracy | Compare skill descriptions vs actual artifact capabilities | Skill claims feature X, artifact doesn't have it |
| Behavioral rules | Check if skill rules are actually enforced | Rule says "never do X", but artifact does X |
| Quality gates | Verify documented quality checks were actually applied | Checklist exists but wasn't followed |
| Artifact-as-skill check | If artifact IS a skill, does it follow skill conventions? | Built a SKILL.md that doesn't match the skill template |

### 7. Documentation Completeness

Are all significant changes properly documented?

| What to check | How | Common drifts |
|---|---|---|
| Changelog coverage | New features/breaking changes have design docs or changelog entries | Feature shipped, no documentation of why or how |
| Progress accuracy | Progress file reflects actual state of work | Code merged, progress still says "in progress" |
| Cross-repo sync | If docs live in a separate repo, both repos are updated | Code committed, design doc not written |
| Template sync | Duplicated docs (e.g., check.md in two locations) are in sync | Source of truth updated, copy stale |
| User-facing doc | Changes to user-visible behavior reflected in README/SKILL.md | CLI flag added, no mention in docs |
| Decision recording | Non-obvious design decisions documented with rationale | "Why did we do X?" — no one remembers |
