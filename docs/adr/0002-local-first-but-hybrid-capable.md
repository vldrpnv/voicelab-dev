# ADR-0002: Local-First but Hybrid-Capable Execution

## Status

Accepted

## Context

Privacy and latency goals push toward local processing. However, local LLMs may not meet quality requirements for all query types, and some heavy tasks benefit from cloud compute. Strict local-only architecture would sacrifice answer quality and limit functionality.

## Decision

Default to local-first execution. Allow hybrid (remote) execution per use case, configured explicitly:

- **Local-only**: privacy-sensitive queries and commands that require no external data.
- **Cloud-allowed**: open-ended questions where a remote LLM provides materially better quality.
- **Cloud-preferred**: heavy reasoning tasks that local compute cannot handle within latency targets.
- **Cached fallback**: graceful degradation to cached results when external dependencies fail.

Hybrid routing is controlled by the Router component via per-scenario policy. Secrets for remote providers are stored locally and never committed to the repository.

## Consequences

- Local path remains the default; remote calls are deliberate, not accidental.
- Answer quality can be optimized per scenario without breaking privacy for sensitive use cases.
- Router policy must classify requests by privacy sensitivity, complexity, and latency budget.
- Remote LLM budget target: < $50/month.
- Architecture avoids vendor lock-in through pluggable provider adapters.
