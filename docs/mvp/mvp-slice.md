# MVP Slice

## Overview

This document defines the minimum viable product scope for VoiceLab. The MVP is intended to validate the core pipeline end-to-end without requiring a fully polished product.

## MVP Decisions

| Aspect | MVP Decision |
|---|---|
| Satellite | One supported satellite path, initially using an existing wake word; custom wake word project starts in parallel. |
| Wake word | Wake word detection on satellite. Custom wake word is not blocking the first technical prototype. |
| Assistant core | Central service on Mac mini. |
| Router | Simple rule-based router; no learned or adaptive policy in MVP. |
| LLM | One remote LLM fallback allowed by configuration. |
| TTS | One TTS path with sanitizer before speech. Interruptibility may begin as partial/stub but must be architecturally designed in from the start. |
| Logging | JSONL structured logs with trace ID and timestamps for every pipeline stage. |
| Testing | Unit tests, sanitizer golden tests, router tests, fake HA/satellite integration tests. |
| CI | Lint, tests, secret scan, basic build. No real hardware required. |
| Deployment | Manual first, then release-triggered deployment to private node. |
| Fault tolerance | At least one cached fallback scenario (e.g., weather). |
| User flagging | Basic "flag last response" command or developer CLI command. |
| Documentation | Global requirements, first ADRs, component READMEs, MVP acceptance criteria. |

## Out of Scope for MVP

- Custom wake word (training starts in parallel, but does not block MVP)
- Phone-call / telephony workflows
- Multi-user profile isolation (designed, but not fully implemented in MVP)
- Cloud-managed or multi-tenant deployment
- Full observability dashboard

## What MVP Proves

1. A satellite or simulated satellite can emit a wake event to the central node.
2. The central node receives a transcript with a trace ID.
3. The router selects between at least two paths (e.g., local and remote LLM).
4. Markdown-heavy LLM output is converted to spoken-friendly text before TTS.
5. A simulated API failure produces a graceful user-facing response, not a raw error.
6. A single interaction can be traced end-to-end from wake event to TTS output.
7. Tests run in CI without real hardware.
8. Secret scanning is active and blocks obvious test secret patterns.
