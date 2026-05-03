# Home Assistant Integration

## Purpose

Adapter between the VoiceLab assistant core and the Home Assistant ecosystem. Handles device commands, state queries, and the HA Voice Preview satellite interface.

## Responsibilities

- Translate assistant action commands into Home Assistant service calls.
- Query HA device and entity state on behalf of the assistant.
- Manage the HA Voice Preview satellite protocol (wake events, audio streaming, playback commands).
- Provide a fake/stub implementation for hardware-independent testing.

## Boundaries

**In scope:**
- HA REST/WebSocket API integration.
- Device command execution and state reads.
- Satellite protocol implementation for HA Voice Preview hardware.

**Out of scope:**
- Wake word detection (satellite responsibility).
- Conversation management or routing.

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet implemented. See `docs/design/` for design notes.
