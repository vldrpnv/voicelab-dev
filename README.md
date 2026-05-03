# voicelab-dev

A local-first, latency-optimized executive assistant that answers broad user questions well, streams speech recognition into a router-driven reasoning/execution pipeline, supports interruptible TTS, and orchestrates connected devices and satellites for complex tasks.

## Repository Structure

```
docs/           Global documentation: contexts, ADRs, requirements, discussions, MVP
firmware/       Satellite and device firmware
services/       Core server-side services (assistant-core, router, tts-output, observability)
integrations/   Adapters to external systems (home-assistant, weather, shopping-list)
wakeword/       Custom wake word training data, experiments, and models
infra/          CI/CD, deployment, Docker, and helper scripts
tests/          Cross-component contract, end-to-end, fixture, and golden tests
.github/        Workflows, issue templates, PR template
```

## Key Documents

- [Product context](docs/contexts/product.md)
- [Architecture context](docs/contexts/architecture.md)
- [Global requirements](docs/requirements/global-requirements.md)
- [MVP slice](docs/mvp/mvp-slice.md)
- [MVP acceptance criteria](docs/mvp/acceptance-criteria.md)
- [ADRs](docs/adr/)
- [Unresolved items and open questions](docs/discussions/unresolved-items-and-open-questions.md)

## Development Principles

See [2026-05-03 discussion summary](docs/discussions/2026-05-03-agent-assisted-development-and-fallbacks.md) for the full development principles list.
