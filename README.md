# voicelab-dev

VoiceLab is a local-first voice assistant platform under active design.

## Repository layout

- `docs/` — global architecture, requirements, ADRs, and open discussion notes.
- `src/` — current assistant-core prototype code.
- `firmware/` — firmware-facing work for Voice Preview and related device changes.
- `satellites/` — satellite-specific protocols, runtimes, and experiments.
- `services/` — backend services that support routing, orchestration, logging, and tool execution.
- `integrations/` — boundaries to Home Assistant and other external systems.
- `wakeword/` — wake word training, evaluation, and model artifacts.
- `infra/` — deployment and environment automation.
- `tooling/` — contributor and agent-support tooling.
- `tests/` — cross-component integration, contract, and regression fixtures.

## Current status

The repository originally contained only the initial context documents and a small `src/` prototype. This update keeps that content intact, adds the missing project structure, and records which issue requirements are already reflected on `main` versus still unresolved.

Start with `docs/README.md`, `docs/adr/0001-repository-structure.md`, and `docs/requirements/project-structure.md`.
