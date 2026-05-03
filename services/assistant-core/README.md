# Assistant Core

## Purpose

The central orchestration service for VoiceLab. Receives transcripts from the satellite, routes them through the reasoning/execution pipeline, and delivers streaming, interruptible spoken responses.

## Responsibilities

- Ingest ASR transcripts (partial and final) from the satellite.
- Maintain conversation session state (history, active tool, timeouts).
- Coordinate with the Router to select a dispatch target.
- Invoke tools and execute multi-step workflows.
- Apply the Quality Layer before delivering responses.
- Emit structured logs with trace IDs and timestamps for every pipeline stage.

## Boundaries

**In scope:**
- Session state management.
- Pipeline orchestration (ASR → Router → LLM/tool → Quality → TTS).
- Tool interface and permission model.
- Fault tolerance and graceful fallback responses.

**Out of scope:**
- Wake word detection (satellite responsibility).
- TTS engine or audio playback (tts-output service).
- Hardware-specific code.

## Key Interfaces

- **Input**: transcript with trace ID from satellite.
- **Output**: spoken-text + display-text + debug-trace response channels.
- **Router**: dispatch decision request/response.
- **Quality Layer**: draft response → quality-annotated response.
- **TTS Output service**: approved spoken text + interrupt flags.

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet implemented. See `docs/design/` for design notes.
