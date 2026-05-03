# Observability Requirements

## Purpose

This document specifies observability, logging, and telemetry requirements for the VoiceLab platform.

## Pipeline Logging

| ID | Requirement | Priority |
|---|---|---|
| OBS-001 | Every stage of the pipeline must be logged: wake event, audio segment ID, ASR partials/final, router decision, LLM prompt/output, sanitizer output, TTS timing, and playback status. | High |
| OBS-002 | All pipeline events must include a monotonic timestamp. | High |
| OBS-003 | All pipeline events for a single user interaction must share a common trace ID. | High |
| OBS-004 | Log format must be structured (JSONL or equivalent). | High |
| OBS-005 | Logs must be emitted to an external telemetry/logging service or a local structured log file. | High |

## Performance Measurement

| ID | Requirement | Priority |
|---|---|---|
| OBS-006 | Each pipeline stage must record its duration. | High |
| OBS-007 | End-to-end latency from wake event to first TTS playback must be measurable from logs. | High |
| OBS-008 | Aggregate latency metrics must be reviewable without real-time access to the system. | Medium |

## Replayability and Debugging

| ID | Requirement | Priority |
|---|---|---|
| OBS-009 | Interactions must be replayable from stored traces (sanitized transcripts, prompts, routing decisions, model outputs). | Medium |
| OBS-010 | Strange or bad responses must be flaggable by the user or developer with trace ID capture. | High |
| OBS-011 | Flagged responses must become regression fixtures to prevent recurrence. | High |

## Quality KPIs

| ID | Requirement | Priority |
|---|---|---|
| OBS-012 | Track user-rated helpfulness, factuality proxy, clarification effectiveness, and task completion rate. | High |
| OBS-013 | Quality KPIs must be reviewable before each release milestone. | Medium |

## Privacy

| ID | Requirement | Priority |
|---|---|---|
| OBS-014 | Logs must not contain raw audio or unredacted personal information by default. | High |
| OBS-015 | Trace IDs must not be spoken aloud to users. | High |

## Open Questions

- Which tracing format: OpenTelemetry, JSONL, or custom?
- Which dashboard or tooling is sufficient for MVP observability review?
- How much pipeline data can be logged without creating an unacceptable privacy risk?
