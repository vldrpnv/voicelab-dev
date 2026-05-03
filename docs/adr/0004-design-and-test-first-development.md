# ADR-0004: Design-First and Test-First Development

## Status

Accepted

## Context

Agent-assisted and human development both benefit from explicit, upfront design and test definitions. Without them:

- Coding agents over-generate and drift outside the intended scope.
- Implementation starts before the expected behavior is agreed.
- Test coverage is added as an afterthought rather than as a design tool.
- Regressions are discovered late and are expensive to fix.

## Decision

All non-trivial changes must follow a design-first, test-first workflow:

### Design before coding

- Every feature that is not a trivial rename or formatting fix must reference a design note, ADR, requirement, or issue with explicit acceptance criteria before any implementation begins.
- If the behavior cannot be described without building it first, create a spike issue (time-boxed research) before a feature issue.

### Test before implementation

- Prefer writing a failing test (or golden fixture) before writing the implementation.
- The test defines the expected behavior and serves as the acceptance criterion.
- Implementation is complete when the test passes and existing tests still pass.
- For exploratory or spike work, tests may follow implementation, but must exist before the work is merged.

### Specs live in the repository

- Acceptance criteria, expected inputs/outputs, and non-goals are versioned alongside the code.
- If behavior changes, the relevant spec, ADR, or test must be updated in the same PR.

### BDD scenarios for user-facing behavior

- Voice UX and assistant workflows are described as Given/When/Then scenarios where useful.
- These scenarios serve as both documentation and test specification.

## Consequences

- Coding agents have bounded, verifiable tasks that are unlikely to produce overreach.
- Regressions become test failures, not user-reported bugs.
- Design decisions are traceable to the code that implements them.
- The project is safe for short-lived coding agents that have no memory between sessions.
