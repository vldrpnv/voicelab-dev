# TTS Output

## Purpose

Converts approved spoken-text responses into interruptible audio playback and manages audio output to satellite devices.

## Responsibilities

- Receive approved spoken text from the assistant core (after sanitization and quality layer).
- Convert text to speech using a configured TTS engine (local or remote).
- Manage streaming audio output to the satellite or playback device.
- Handle cut-in interrupts: stop current playback when the user speaks.
- Emit playback status events for logging and pipeline tracing.

## Boundaries

**In scope:**
- TTS engine integration (local-first: Coqui, Edge TTS; remote: optional).
- Audio output and interrupt handling.
- Playback status events.

**Out of scope:**
- Response generation or sanitization (assistant-core responsibility).
- Wake word detection or audio capture.

## Key Interfaces

- **Input**: `spoken_text` with interrupt flag, voice metadata, and trace ID.
- **Output**: audio playback, interrupt events, playback status log entries.

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet implemented. See `docs/design/` for design notes.
