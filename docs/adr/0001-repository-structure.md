# ADR-0001: Small-Scale Monorepo Structure

## Status

Accepted

## Context

VoiceLab is a local-first executive assistant platform spanning firmware, services, integrations, tooling, and documentation. Each area has different constraints, testability needs, and development cadence. A flat structure would conflate these concerns. A full-scale multi-repo or complex monorepo build system would add friction before the system is stable.

## Decision

Use a small-scale monorepo with clearly separated top-level areas:

```
docs/           Global planning: ADRs, requirements, roadmap, MVP, process rules
firmware/       Satellite and device firmware
services/       Core server-side services (assistant-core, router, tts-output, observability)
integrations/   Adapters to external systems (home-assistant, weather, shopping-list)
wakeword/       Custom wake word training data, experiments, and models
infra/          CI/CD, deployment, Docker, and helper scripts
tests/          Cross-component contract, end-to-end, fixture, and golden tests
.github/        Workflows, issue templates, PR template
```

Each component directory contains:
- `README.md` — component purpose, boundaries, and status
- `docs/adr/` — component-local architectural decision records
- `docs/design/` — design notes and specs
- `tests/` — component-level tests

## Consequences

- Component boundaries are explicit and navigable without reading the full repository.
- Each component can evolve independently with its own local ADRs.
- Global cross-cutting concerns (security, observability, process) are recorded once and referenced.
- External contributors and coding agents can scope their work to one bounded context.
- No build-system coupling is introduced; each service can have its own language/tooling.
