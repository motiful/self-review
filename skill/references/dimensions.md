# Dimension Details

Detailed checks for all 7 audit dimensions. Dimensions 1-3 are Progress-centric (highest priority). Dimensions 4-7 are cross-pillar deep checks.

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
| Verification depth | Check artifact passes its own success criteria, not just exists | Marked done, artifact exists, but doesn't actually work |

#### Artifact Verification Depth

Checking "does the artifact exist?" is necessary but insufficient. Dimension 2 must both **assess** and **execute** verification to the appropriate depth.

| Level | What it checks | Code example | Non-code example |
|-------|---------------|-------------|-----------------|
| **L1 Exists** | Artifact was produced | File exists | Video/article generated |
| **L2 Build** | Follows conventions and standards | tsc passes, lint clean | Format correct, axes labeled |
| **L3 Integration** | Business logic works correctly | Runtime execution, CLI commands produce expected output | Content reads correctly, config takes effect |
| **L4 E2E** | Meets design intent end-to-end | Full user workflow verified | Complete user scenario validated |

**Minimum bar: L3 (Integration).** L2-only (compilation) is insufficient for any artifact with behavioral changes. L4 when design expectations demand it.

#### Verification Execution Protocol

Self-review MUST execute verification, not just report that it's missing. The process:

1. **Determine design expectation**: Read the design/progress docs. What does "done" mean for this artifact? "Compiles" vs "runs correctly" vs "handles edge cases" are different bars.

2. **Execute tests at the appropriate level**:
   - L2 (Build): Run the build/compile/lint command. Report pass/fail.
   - L3 (Integration): Run the artifact. For code: execute CLI commands, call functions, verify output. For configs: apply and check effect. For content: verify it renders/reads correctly.
   - L4 (E2E): Run the full user workflow. For a CLI tool: simulate a real usage scenario. For an API: call it with real inputs and verify responses.

3. **Report results quantitatively**:
   - What was tested (specific commands/scenarios)
   - What passed / what failed (with actual output)
   - Current verification level achieved (L1/L2/L3/L4)
   - Gap to design expectation (e.g., "design expects L4, achieved L3 — E2E not tested")

4. **If a test cannot be automated**, you must:
   - Exhaust all options first. "I can't test this" is often wrong — investigate before declaring it untestable.
   - If truly untestable (requires human interaction, costs excessive tokens, needs external services): document exactly what needs manual verification and surface it as a **human-test-required** item in the report.

#### Verification Depth by Artifact Type

| Artifact type | Minimum level | How to verify |
|---------------|--------------|---------------|
| Code (library/module) | L3 | Import and call key functions, verify return values |
| Code (CLI command) | L3 | Execute the command with real args, check output |
| Code (daemon/service) | L3 | Start it, send requests, verify responses |
| Code (bug fix) | L3 | Reproduce the original bug scenario, verify it's fixed |
| Configuration | L3 | Apply the config, verify the system behaves differently |
| Skill/documentation | L2 | Verify structure, check internal links resolve, no stale references |
| Infrastructure (CI/CD) | L3 | Trigger the pipeline or simulate trigger, verify it runs |

**L4 (E2E) is required when**: the design doc, progress, or acceptance criteria explicitly state end-to-end behavior, or when the artifact is a user-facing workflow with multiple interacting components.

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
