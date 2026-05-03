# ADR-0003: Hardware-Independent Development

## Status

Accepted

## Context

VoiceLab targets real hardware (Mac mini, Home Assistant Voice Preview satellite devices). However, making day-to-day development and CI dependent on physical hardware creates serious problems:

- External contributors and coding agents cannot run tests without the specific home setup.
- CI cannot run without hardware access.
- Bugs are hard to reproduce without the exact device state.
- Development speed is limited by hardware availability.

## Decision

All development and CI must be hardware-independent by default.

Rules:
- Unit and component tests use fakes, stubs, and mocks for all hardware interfaces.
- Contract tests define the expected interface behaviour for each hardware integration point.
- End-to-end tests use a simulated pipeline that replaces audio capture with pre-recorded text fixtures.
- Golden tests (sanitizer output, router decisions, TTS-safe formatting) run without any device.
- Real hardware validation is reserved for final acceptance testing only, not CI.
- CI must pass on a standard cloud runner without any hardware credentials or devices.

Fake implementations must:
- satisfy the same interface contract as the real hardware adapter,
- behave deterministically for test input,
- be replaceable by the real adapter without changing the code under test.

## Consequences

- Any developer or coding agent can run the full test suite on a standard laptop.
- CI pipelines are stable and do not depend on home network availability.
- Hardware integration points are defined as explicit contracts before the real hardware is connected.
- Real-hardware test sessions are documented separately and not gated as CI requirements.
