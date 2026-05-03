# Observability

## Purpose

Provides structured logging, telemetry, and tracing infrastructure for the VoiceLab pipeline.

## Responsibilities

- Define and enforce the structured log format (JSONL) used across all services.
- Assign and propagate trace IDs for each user interaction.
- Collect and export pipeline stage durations and latency metrics.
- Provide utilities for flagging bad responses and capturing regression traces.
- Enforce privacy constraints in logs (redaction, retention policies).

## Boundaries

**In scope:**
- Log schema definition and shared logging utilities.
- Trace ID generation and propagation.
- Telemetry export configuration.
- Regression fixture capture utilities.

**Out of scope:**
- External log storage or dashboard (infrastructure concern).
- Audio recording or transcript storage beyond structured log events.

## Key Outputs

- Per-interaction JSONL log entries with trace ID, timestamps, stage durations.
- Flagged-response capture with full pipeline artifact snapshot.

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet implemented. See `docs/design/` for design notes.
