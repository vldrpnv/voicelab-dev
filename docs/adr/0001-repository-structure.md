# ADR-0001: Repository structure

- Status: Accepted
- Date: 2026-05-03

## Context

`origin/main` already captured the product, domain, architecture, and constraint context in `docs/contexts/`, and it included a small assistant-core prototype in `src/`. It did not yet provide the explicit monorepo structure requested in the project-structure issue: separate spaces for firmware, satellites, assistant core, services, integrations, infrastructure, tooling, wake word work, shared tests, and durable documentation lanes for requirements, ADRs, and unresolved discussions.

## Decision

Adopt the following top-level layout:

- `docs/` for global documentation
  - `docs/contexts/` for seed context material already on `main`
  - `docs/adr/` for accepted repository-wide decisions
  - `docs/requirements/` for versioned requirements and structure guidance
  - `docs/discussions/` for unresolved items and challenge questions
- `src/` for the current assistant-core prototype until code naturally splits into dedicated packages/services
- `firmware/`, `satellites/`, `services/`, `integrations/`, `wakeword/`, `infra/`, `tooling/`, and `tests/` as the primary bounded contexts for future implementation work

## Consequences

- Existing content remains valid and does not need to be moved prematurely.
- The repository now exposes the intended development tracks directly in the file tree.
- Future implementation work should add local README/design/ADR/test material inside the relevant component directory instead of expanding global docs only.
- Unresolved questions from the project-structure discussion remain in `docs/discussions/project-structure-open-items.md` until promoted into requirements or ADRs.
