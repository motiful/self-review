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
