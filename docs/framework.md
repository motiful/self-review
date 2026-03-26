# The Framework: Principles, Pillars, and Dimensions

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

**Cross-pillar (always run by default):**
4. **Design <> Artifact** — Does the output match the design?
5. **Design <> Skill** — Do our methods support our design goals?
6. **Artifact <> Skill** — Does the output follow established methods?

## Verification Depth

Dimension 2 verifies artifacts at 4 levels of depth — L1 (Exists), L2 (Build), L3 (Integration), L4 (E2E). Default minimum is L3 for code and configuration, L2 for documentation and content. L4 when acceptance criteria explicitly require end-to-end verification.

For the complete verification depth table with per-artifact-type minimums, see `references/dimensions.md` § Verification Depth by Artifact Type.
