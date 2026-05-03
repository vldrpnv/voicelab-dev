# Unresolved Items and Open Questions

This document collects items from the initial requirements discussion that remain unresolved, plus the "Key Blind Spots to Keep Challenging" questions intended to prevent common pitfalls in this project.

---

## Unresolved Open Questions by Area

### Product Scope

- Which first workflows best prove the platform's executive assistant value?
- Which organic workflows are MVP-critical (shopping list, calendar, planning, etc.)?
- What latency vs. patience tradeoff is acceptable for slow-speaker accommodation?
- Should personality configuration be global, per-user, or per-context?
- Which child-related use cases are allowed in MVP, and what does age-aware response mode look like?

### Satellite and Firmware

- Which satellite hardware variants are supported first?
- Which wake word engine will be used initially (openWakeWord, Porcupine, custom model, other)?
- What is the target custom wake word? Which language/accent variants are needed?
- What is the acceptable false activation rate for household use?
- How far can the Home Assistant Voice Preview firmware be modified without fighting upstream assumptions?
- Which firmware changes are mandatory vs. nice-to-have?
- Is audio streamed to the central node, or does the satellite do partial ASR locally?

### Assistant Core

- What exact latency budgets are realistic on a Mac mini with satellites?
- Should interim acknowledgements be spoken, sound-based, LED-based, or configurable?
- Which commands must stay below 2 seconds?
- Which routing dimensions are required in MVP (complexity, urgency, privacy, capability)?
- Which requests are privacy-sensitive enough to forbid cloud routing?
- Which tools are first: shopping list, calendar, HA control, Spotify, notes?
- What is the minimum useful behavior when central services are degraded?

### Output and Quality

- Should the TTS sanitizer be rule-based, LLM-based, or both?
- How should code blocks, tables, URLs, and lists be handled in spoken mode?
- Which clients can display visual companion content alongside audio?
- How will the user flag issues by voice (e.g., "flag that" command)?
- Where should golden test fixtures live?

### Logging and Observability

- Which tracing format should be used: OpenTelemetry, JSONL, or custom?
- Which dashboard or tooling is sufficient for MVP observability?
- How much pipeline data can be logged without an unacceptable privacy risk?
- Should trace IDs ever be spoken? (Current assumption: no.)
- What is the default log retention duration?

### Security and Privacy

- What is the policy for multi-user isolation boundaries (config, history, runtime quotas)?
- Should transcript retention be configurable by user or profile, and for how long?
- What is the minimum identity confidence threshold before using private user context?

### Development Process

- What change size requires an ADR?
- How strictly should TDD be enforced for prototypes vs. production code?
- Should BDD scenarios use Gherkin formally or simple Markdown?

### Infrastructure

- What is the exact private-network deployment model (push vs. pull, trigger mechanism)?
- What are cache expiration and privacy rules for fallback data?
- What details should be logged vs. only accessible in an admin/debug UI?

### Quality KPIs and Release

- Which minimum quality thresholds should gate production rollout for executive-assistant capabilities?
- Which quality metrics should be used to define "respond WELL" (factuality, task completion rate, user-rated helpfulness)?

---

## Candidate ADRs Not Yet Created

The following ADRs were identified in the requirements discussion but not yet created. They should be created when the relevant component or cross-cutting concern is first worked on:

| ADR | Proposed Title | Trigger |
|---|---|---|
| ADR-0006 | Hardware-independent testing strategy | When setting up CI or writing first hardware-adjacent tests |
| ADR-0007 | No secrets in repository | When setting up CI secret scanning |
| ADR-0008 | Private-network deployment model | When defining the deployment pipeline |
| ADR-0009 | Pipeline tracing and timestamping | When implementing logging or observability |
| ADR-0010 | Spoken-output sanitization layer | When building TTS output or the sanitizer |
| ADR-0011 | Graceful fallback and error-language policy | When implementing first external integration |
| ADR-0012 | Per-user assistant profiles and voice identification | When beginning multi-user support |

---

## Key Blind Spots to Keep Challenging

These questions are designed to challenge assumptions that commonly lead to poor outcomes in voice assistant projects:

| Blind Spot | Challenge Question |
|---|---|
| Local-first dogmatism | Is this scenario actually better locally, or only ideologically local? |
| Hardware coupling | Can a third-party developer test this without a Mac mini and satellites? |
| Wake word complexity | Are we treating custom wake word training as a real product workstream with metrics? |
| TTS formatting | Would this response sound good when spoken aloud? |
| Raw errors | What does the user hear when this dependency fails? |
| Agent overreach | Can an autonomous coding agent solve this task without breaking something else? |
| Latency measurement | Do we have actual measurements, or are we guessing latency is acceptable? |
| Quality definition | What does "respond WELL" mean in concrete, measurable terms for this scenario? |
| Privacy creep | Are we logging more than we need, and is it safe? |
| Scope creep | Is this feature in the MVP slice, or are we building ahead of validated need? |
| Multi-user assumptions | Does this work correctly when two different users interact on the same day? |
| Fallback coverage | Which scenarios have a cached or degraded fallback, and which ones fail silently? |
