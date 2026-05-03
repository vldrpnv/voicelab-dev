# MVP Acceptance Criteria

## Purpose

This document defines the acceptance criteria that must be met for MVP readiness. Each criterion corresponds to a testable, observable outcome.

## Acceptance Criteria

| Requirement | Acceptance Criteria |
|---|---|
| Wake detection path exists | A satellite or simulated satellite can emit a wake event to the central node. |
| Assistant receives request | Central node receives a text transcript or audio-derived transcript with a valid trace ID. |
| Router works | Router selects between at least two dispatch paths (e.g., local simple response and remote LLM). |
| TTS-safe output | Markdown-heavy input is converted to spoken-friendly text before reaching TTS. |
| Fallback works | A simulated API failure produces a graceful, humanly phrased user-facing response — not a raw error. |
| Logs are useful | A single interaction can be traced end-to-end from wake event to final TTS output using structured logs. |
| Timing is measurable | Logs show duration of each major pipeline stage. |
| Tests run in CI | The GitHub Actions workflow runs all tests without requiring real hardware. |
| Secrets are blocked | Secret scanning runs in CI and fails on obvious test secret patterns. |
| Docs are linked | Each MVP issue and PR links to the relevant requirement and ADR files. |

## PR Checklist

- [ ] The change is linked to an issue or requirement.
- [ ] Relevant ADRs/design records were consulted.
- [ ] The change stays within the intended component boundaries.
- [ ] Tests were added or updated.
- [ ] CI passes.
- [ ] No secrets, tokens, private hostnames, or local credentials were committed.
- [ ] Logs/traces were updated if pipeline behavior changed.
- [ ] Spoken-output behavior was considered if user-facing text changed.
- [ ] Fallback behavior was considered if external dependencies are involved.
- [ ] Documentation was updated where needed.
