# M0 — Walking Skeleton

## Goal

Build the smallest useful technical path through the system. This milestone validates the architecture shape without real hardware, real providers, or production-quality components.

The skeleton is intentionally fake at every layer. Each fake layer will be replaced in a later milestone.

## Target Pipeline

```
simulated text request
  → assistant-core entry point
  → rule-based router stub
  → fake executor / response generator
  → spoken-output sanitizer
  → JSONL trace log
  → text output (no real TTS)
```

## In Scope

- Simulated text request input model (no audio, no satellite, no hardware)
- `assistant-core` package with a minimal entry point
- Simple rule-based router (at least two deterministic dispatch paths)
- Fake executor that returns pre-defined test responses
- Spoken-output sanitizer with golden test fixtures
- Trace ID assigned at request entry and propagated through all stages
- Timestamped JSONL log entry for each pipeline stage (wake, route, execute, sanitize, output)
- CLI command to run one simulated interaction end-to-end
- Unit tests for each component
- CI workflow that runs tests and secret scanning on every push

## Out of Scope

- Real satellite firmware or wake word hardware
- Real ASR (speech-to-text) from audio input
- Real TTS (text-to-speech) playback or audio output
- Real Home Assistant device control
- Real LLM API calls (OpenAI, Anthropic, local models, etc.)
- Multi-user profiles or voice identification
- Deployment automation
- Long-term memory or database persistence
- Cloud/local model comparison or benchmarking

## First Components

| Component | Location | Status |
|---|---|---|
| Simulated request model | `services/assistant-core/` | Planned |
| Router stub | `services/router/` | Planned |
| Fake executor | `services/assistant-core/` | Planned |
| Spoken-output sanitizer | `services/tts-output/` | Planned |
| Trace/JSONL logger | `services/observability/` | Planned |
| CLI entry point | `services/assistant-core/` | Planned |

## Test Expectations

- Unit tests exist for every component.
- Golden fixtures exist for sanitizer input/output pairs (at least 5 examples).
- Tests cover the fake end-to-end path from simulated request to JSONL trace entry.
- All tests run without network access or hardware credentials.
- CI runs all tests and secret scan on every push.

## Hardware Independence

All M0 work must run on a standard laptop or cloud CI runner without any hardware, device credentials, or API keys.

See [ADR-0003: Hardware-Independent Development](../adr/0003-hardware-independent-development.md).

## Success Criteria

| Criterion | Required Result |
|---|---|
| Simulated input exists | A test or CLI can submit a fake text request |
| Router works | The router classifies the request and selects a dispatch path |
| Fake executor works | At least one fake response is returned for the routed request |
| Sanitizer works | Markdown and technical artifacts in a fake response are converted to spoken-safe text |
| Trace exists | Every request has a trace ID; all pipeline stages emit a timestamped JSONL log entry |
| Tests pass | All unit and golden tests pass in CI |
| CI is green | GitHub Actions runs tests and secret scan without hardware |
| Docs exist | This document, at least one ADR, and component READMEs are in place |

## Explicit Non-Goals for M0

These will be addressed in later milestones but must not be designed prematurely:

- Perfect TTS quality or voice naturalness
- Accurate intent classification
- Real routing policy logic
- Production-grade error handling beyond fake fallback messages
- Performance optimization or latency tuning
- Security hardening beyond the no-secrets rule
