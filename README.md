# voicelab-dev

A local-first, latency-optimized executive assistant. Built layer by layer, starting from a walking skeleton.

> Current focus: **M0 — Walking Skeleton** — a minimal end-to-end pipeline with fake components, proving the architecture before building the real system.

## Repository Structure

```
docs/           Global planning: roadmap, MVP slice, ADRs, requirements, process rules
firmware/       Satellite and device firmware
services/       Core server-side services (assistant-core, router, tts-output, observability)
integrations/   Adapters to external systems (home-assistant, weather, shopping-list)
wakeword/       Custom wake word training data, experiments, and models
infra/          CI/CD, deployment, Docker, and helper scripts
tests/          Cross-component contract, end-to-end, fixture, and golden tests
.github/        Workflows, issue templates, PR template
```

## Start Here

| Document | Purpose |
|---|---|
| [docs/roadmap.md](docs/roadmap.md) | Workstreams, milestones, and planning priorities |
| [docs/mvp-slice.md](docs/mvp-slice.md) | M0 walking skeleton scope and success criteria |
| [docs/development-process.md](docs/development-process.md) | How to plan and execute issues |
| [docs/issue-planning-rules.md](docs/issue-planning-rules.md) | Rules for creating issues that are safe for humans and agents |
| [docs/adr/](docs/adr/) | Global architectural decision records |
| [docs/mvp/m0-walking-skeleton.md](docs/mvp/m0-walking-skeleton.md) | Detailed M0 spec and acceptance criteria |
