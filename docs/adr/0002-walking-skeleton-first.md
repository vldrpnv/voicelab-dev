# ADR-0002: Walking Skeleton First Strategy

## Status

Accepted

## Context

The VoiceLab platform is intentionally large: it spans satellite firmware, custom wake word training, Home Assistant integration, a routing layer, LLM orchestration, TTS output, and observability. Starting with any one of these full production components risks:

- Blocking external contributors and coding agents on hardware or service dependencies.
- Building components that are hard to test before end-to-end behavior is verified.
- Designing in isolation without running feedback from the integrated system.
- Accumulating complexity before the system shape is confirmed.

The alternative is to start with a walking skeleton.

## Decision

The first implementation milestone (M0) must be a walking skeleton: a minimal end-to-end version of the system using fake/stub implementations for every component that has hardware, provider, or service dependencies.

The target pipeline for M0:

```
simulated text request
  → assistant-core entry point
  → rule-based router stub
  → fake executor / response generator
  → spoken-output sanitizer
  → JSONL trace log
  → text output (no real TTS)
```

Nothing in M0 requires:
- real satellite or wake word hardware,
- real ASR or TTS engines,
- real Home Assistant device control,
- real LLM API calls,
- real deployment automation,
- multi-user support.

Each fake layer must respect the same interface contract as the eventual real implementation, so real components can replace fakes incrementally without rewriting the skeleton.

## Consequences

- All M0 work can be done on any laptop without hardware or cloud credentials.
- The shape of the architecture is validated before real complexity is added.
- Tests can be written against fakes and remain valid as fakes are replaced.
- Future milestones replace one fake layer at a time, reducing risk.
- The project becomes manageable: each step is a controlled replacement of one fake with one real component.
