# Dimension Details

Detailed checks for each of the 4 audit dimensions. Each dimension compares two pillars for drift.

---

## 1. Design ↔ Artifact

Does what was built match what was designed?

| What to check | How | Common drifts |
|---|---|---|
| Spec vs output | Compare design specs/requirements against actual deliverables | Feature designed but not built, or built differently |
| Architecture adherence | Compare designed structure vs actual structure (imports, layers, file layout) | Layer bypass, unauthorized dependency |
| Naming consistency | Check artifact names match design vocabulary | Design says "deck", artifact says "task" |
| Decision compliance | For each recorded decision, verify artifact follows it | Decision made but artifact does the opposite |
| Rejected alternatives | Verify artifact doesn't use explicitly rejected approaches | Rejected approach snuck in during execution |
| Scope boundaries | Compare designed scope vs what artifact actually covers | Scope creep or under-delivery |

---

## 2. Methodology ↔ Artifact

Does the output follow the established methods and standards?

| What to check | How | Common drifts |
|---|---|---|
| Process compliance | Compare skill/workflow docs against actual execution evidence | Methodology says "always review", but no review evidence |
| Standards adherence | Check artifact against documented standards (style guides, conventions) | Standard exists but artifact violates it |
| Template conformance | Compare templates vs what artifact actually produces | Template updated, artifact still uses old format |
| Skill accuracy | Compare skill descriptions vs actual artifact capabilities | Skill claims feature X, artifact doesn't have it |
| Behavioral rules | Check if methodology rules are actually enforced | Rule says "never do X", but artifact does X |
| Quality gates | Verify documented quality checks were actually applied | Checklist exists but wasn't followed |

---

## 3. Design ↔ Progress

Are plans and trajectory aligned with design intent?

| What to check | How | Common drifts |
|---|---|---|
| Phase alignment | Compare progress phase status vs design milestones | Progress says Phase 2 done, but design Phase 2 goals not met |
| Priority ordering | Verify progress priorities match design priorities | Design says A before B, progress has B first |
| Scope consistency | Compare planned scope in progress vs design scope | Design expanded, progress still lists old scope |
| Deferred items | Verify deferred items are tracked somewhere | Silently dropped — not in progress, not in design |
| Direction check | Is the trajectory moving toward the design vision? | Progress shows activity, but drifting from design goals |
| Dependency ordering | Check progress respects design's dependency chain | Progress shows Phase 3 item next, but Phase 2 dependency unfinished |

---

## 4. Progress ↔ Artifact

Does claimed status match actual deliverables?

| What to check | How | Common drifts |
|---|---|---|
| Completion claims | Cross-ref "done" items in progress vs actual artifacts | Marked done but artifact incomplete or missing |
| Pending accuracy | Verify "pending" items are actually unstarted | Work started but progress not updated |
| Artifact inventory | Check for artifacts not reflected in progress | Built something, forgot to track it |
| Status freshness | Compare artifact timestamps vs progress update timestamps | Artifact changed after last progress update |
| Deliverable evidence | For each claimed deliverable, verify it exists and works | Progress claims "tests pass" but tests don't exist |
| Gap detection | Items in progress with no corresponding artifact | Planned but never started, or started and abandoned |
