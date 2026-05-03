# Discussion Summary: Agent-Assisted Development and Architecture Decisions

**Date:** 2026-05-03  
**Source:** VoiceLab development requirements discussion

---

## Purpose

This document records the key requirements, assumptions, risks, and process decisions discussed for the VoiceLab project. It serves as a durable reference for both human contributors and coding agents. For open and unresolved items, see [unresolved-items-and-open-questions.md](./unresolved-items-and-open-questions.md).

---

## Product Scope

- The project is a local-first executive assistant platform, not only a Home Assistant voice integration.
- Distinct development tracks: firmware, satellites, assistant core, services, infrastructure, and tooling.
- The assistant must support natural, organic workflows — not only rigid command-response interactions.
- Slow user formulation must be tolerated; aggressive interruption degrades UX.
- The assistant must have a defined, consistent personality.
- Multi-user (family) operation is required, with separate assistant state, preferences, and access boundaries.
- Children's questions should eventually be answered in an age-aware way.

## Satellite

- Satellite development is a distinct project/component with its own firmware, docs, ADRs, and interfaces.
- Wake word recognition must happen on the satellite device.
- The final product must not depend on standard wake words ("Hey Nabu", Mycroft defaults).
- Custom wake word training is a separate parallel project with its own learning curve, tooling, data collection, and model evaluation.
- Wake word quality must be measured with FAR/FRR metrics under realistic household noise conditions.

## Firmware

- Starting point: Home Assistant Voice Preview firmware.
- Firmware must remain flexible — custom interactions, streaming, routing, and LED/sound feedback may require changes.
- Streaming capabilities must be evaluated; the firmware should support partial transcript or audio streaming to the central node.

## Assistant Core

- Timing is a first-class architectural concern; latency budgets and timestamped pipeline logging are mandatory.
- Early acknowledgement ("I'm checking that") must be emitted for longer tasks.
- Routing must classify by complexity, urgency, privacy, and capability.
- Local-first, but hybrid local/cloud execution is supported and chosen deliberately per use case.
- Tool orchestration and multi-step workflow execution are required for executive assistant value.
- Fault tolerance must be built into every major step; raw API errors must never reach the user.
- Graceful degraded responses must be supported (e.g., cached weather forecast when API fails).

## Output

- TTS-safe formatting is required: Markdown, code fences, bullets, URLs, and symbols must not reach TTS.
- Spoken and visual/logged output must be separate response channels.
- Strange or bad responses must be flaggable and become regression test fixtures.

## Logging

- Every pipeline stage must be logged with timestamps and a shared trace ID per interaction.
- Performance measurement is mandatory from day one; latency optimization must be measurement-based.
- Requests should be replayable where privacy permits.
- Logs must be privacy-aware: redaction, retention policies, and local-only storage.

## Development Process

- Design before implementation: nontrivial changes reference a design note, ADR, or requirement.
- Specs live in the repository and are versioned with the code.
- Test-first development is preferred where practical (red test → implementation → green test).
- BDD scenarios in natural language are encouraged for user-facing voice workflows.
- CI must cover lint, tests, secret scanning, and basic build.
- Changes must be small and reviewable; coding agents work in bounded, traceable increments.

## Infrastructure and Deployment

- Deployment is initially manual, then automated as release-triggered deployment to a private node.
- Docker/container deployment must be supported.
- Linux compatibility is required in the near term.
- Private-network deployment model must be defined.

---

## Development Principles Summary

| Principle | Meaning |
|---|---|
| Design before implementation | Nontrivial changes should reference a design note, ADR, or requirement. |
| Specs live in the repository | Requirements and acceptance criteria are versioned with the code. |
| ADRs are both global and local | System-wide decisions go into global docs; component-specific decisions live near the component. |
| Keep agent context small | Every task should point to the minimum relevant files, not the whole repository. |
| Test first where practical | Prefer red test, then implementation, then green test. |
| Hardware-independent by default | Development and CI should not require the real home setup. |
| Real hardware is for final validation | Target devices are used for final acceptance and UX checks, not daily CI dependency. |
| No secrets in code | Secrets are never committed; scanning and review enforce this. |
| Fault tolerance is product behavior | Failures must degrade gracefully and never expose raw infrastructure errors to users. |
| Spoken output is a separate product surface | TTS-safe text is not the same as Markdown or debug output. |
| Measure timing from day one | Every stage should produce timing data. |
| Bad responses become tests | Flagged strange outputs should become regression fixtures. |
| Local-first, not local-dogmatic | Local execution is preferred, but hybrid execution can be chosen deliberately per use case. |
| Small PRs and small agent tasks | Autonomous or human contributors should work in bounded, reviewable increments. |
| Documentation changes with behavior | If behavior changes, specs/ADRs/tests should be updated. |
