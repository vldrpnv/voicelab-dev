# ADR-0001: Repository Structure for Small-Scale Monorepo

## Status

Accepted

## Context

VoiceLab is a local-first executive assistant platform spanning firmware, services, integrations, tooling, and documentation. Each area has different constraints, testability needs, and development cadence. A flat single directory would conflate these concerns.

## Decision

Adopt a small-scale monorepo with the following top-level layout:

```
docs/           Global documentation: contexts, ADRs, requirements, discussions, MVP
firmware/       Satellite and device firmware
services/       Core server-side services (assistant core, router, TTS output, observability)
integrations/   Adapters to external systems (Home Assistant, weather, shopping list)
wakeword/       Custom wake word training data, experiments, and models
infra/          CI/CD, deployment, Docker, and helper scripts
tests/          Cross-component contract, end-to-end, fixture, and golden tests
.github/        Workflows, issue templates, PR template
```

Each component directory contains:
- `README.md` — component purpose, boundaries, and usage
- `docs/adr/` — component-local architectural decision records
- `docs/design/` — design notes and specs
- `tests/` — component-level tests

Global ADRs and cross-cutting requirements live in `docs/`.

## Consequences

- Boundaries between firmware, services, integrations, and tooling are explicit.
- Each component can evolve at its own pace with its own local ADRs.
- Global concerns (security, observability, quality) are documented once and referenced.
- External developers and coding agents can navigate to the relevant bounded context without reading the entire repository.
