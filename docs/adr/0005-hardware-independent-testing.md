# ADR-0005: Hardware-Independent Testing Strategy

## Status

Accepted

## Context

Development and CI must not depend on the physical Mac mini, Home Assistant Voice Preview hardware, or satellites being available. Requiring real hardware for every test would block external contributors, coding agents, and automated CI runs.

## Decision

All development and CI testing must be hardware-independent by default:

- Unit tests and component tests use fakes, stubs, and mocks for hardware interfaces (audio devices, HA integration, satellites).
- Contract tests define expected interface behaviour for each integration point.
- End-to-end tests may use a simulated pipeline that replaces audio capture with pre-recorded fixtures.
- Golden tests cover sanitizer output, router decisions, and TTS-safe formatting without any hardware.
- Real hardware validation (Home Assistant devices, satellites) is reserved for final acceptance testing only, not CI.

Fake implementations must faithfully represent the interface contract of the real hardware so that tests remain meaningful.

## Consequences

- Any developer or coding agent with a standard laptop can run the full test suite.
- CI pipelines run without hardware access.
- Interface contracts between hardware adapters and core services must be explicitly defined.
- Real-hardware test sessions are documented separately and not automated in CI.
