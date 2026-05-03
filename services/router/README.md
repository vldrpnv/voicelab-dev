# Router

## Purpose

The Router classifies incoming requests and decides which execution path to use: local model, remote LLM, tool/satellite, or cached fallback.

## Responsibilities

- Classify request by complexity, urgency, privacy sensitivity, and required capability.
- Apply routing policy to select a dispatch target and emit a dispatch decision.
- Emit an interim acknowledgement hint when a long-running path is selected.
- Log routing decisions with trace ID and timestamp.

## Boundaries

**In scope:**
- Routing policy definition and evaluation.
- Decision logging.
- Routing heuristics (rule-based in MVP; learned policy later).

**Out of scope:**
- Executing the routed request (Dispatcher/Orchestrator responsibility).
- Managing conversation state.

## Routing Paths (MVP)

| Path | When used |
|---|---|
| Local fast path | Simple commands; no external data needed; privacy-sensitive. |
| Remote LLM | Open-ended questions where quality matters more than strict locality. |
| Tool/satellite | Requests requiring external action or data retrieval. |
| Cached fallback | When a dependency is unavailable; use last-known good data. |

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet implemented. See `docs/design/` for design notes.
