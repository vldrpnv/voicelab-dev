# Development Process

## Overview

VoiceLab uses a design-first, test-first, and walking-skeleton-first development process. The goal is to make each unit of work safe, small, and executable by humans or coding agents.

See [ADR-0004](adr/0004-design-and-test-first-development.md) for the rationale.

---

## Planning Rhythm

### Weekly Planning

1. Pick one milestone.
2. Pick no more than 5 active issues.
3. Ensure every issue has acceptance criteria.
4. Ensure at least 3 issues are small enough for agent or external developer execution.
5. Keep one issue for documentation cleanup.
6. Keep one issue for tests/observability.

### Session or Daily Planning

**Before starting:**
1. Choose one issue.
2. Read only the relevant docs (linked in the issue).
3. Define expected output.
4. Run or write the failing test.
5. Implement the smallest change.
6. Run tests.
7. Update docs if behavior changed.
8. Commit.

**After finishing:**
1. What changed?
2. What test proves it?
3. What document or ADR needs updating?
4. What is the next smallest issue?

---

## Workstream Categories

Before creating or starting any issue, classify the idea:

| Category | Meaning | Action |
|---|---|---|
| `Now` | Needed for the current milestone | Create/attach to current milestone |
| `Soon` | Needed after current milestone | Add to next milestone |
| `Parallel` | Separate workstream, not blocking current | Create separate milestone/project |
| `Later` | Valuable but not needed soon | Add to backlog |
| `Research` | Unknown feasibility | Create spike issue |
| `Reject for now` | Too distracting or premature | Record in discussion notes only |

---

## Issue Shape Rules

See [issue-planning-rules.md](issue-planning-rules.md) for the full set of rules.

Short version:
- One issue changes one thing.
- Every issue states what is out of scope.
- Every issue includes acceptance criteria.
- Every implementation issue names relevant docs.
- Every issue states whether it is agent-safe.

---

## PR Rules

Use the PR template in `.github/PULL_REQUEST_TEMPLATE.md`. Key checks:
- The change is linked to an issue or requirement.
- Relevant ADRs were consulted.
- Tests were added or updated.
- CI passes.
- No secrets were committed.
- Documentation updated if behavior changed.

---

## Avoiding Common Traps

| Trap | Why to avoid it |
|---|---|
| Starting with real firmware | Too many unknowns too early |
| Starting with custom wake word | Becomes a long research project that blocks nothing if deferred |
| Starting with HA integration | Hardware/local setup slows external development |
| Starting with cloud/local model comparisons | Useful later, distracting during skeleton phase |
| Starting with deployment automation | Needs something stable to deploy first |
| Starting with multi-user identity | Important, but not needed for the skeleton |
| Designing the perfect architecture upfront | A working traceable skeleton is more valuable than a perfect design |
| Creating 100 backlog items | Creates false progress and cognitive load |
| Letting agents modify broad areas | High risk before structure and tests exist |

---

## Component Boundaries

Each component in `services/`, `integrations/`, `firmware/`, and `wakeword/` is a bounded context. Changes should stay within one component unless they are explicitly cross-cutting.

Cross-cutting concerns (security, observability, quality) are documented once in global ADRs and referenced from components.

See [ADR-0001](adr/0001-repository-structure.md) for the full layout.
