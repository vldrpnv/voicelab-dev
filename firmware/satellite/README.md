# Satellite Firmware

## Purpose

This component contains firmware for VoiceLab satellite devices (Home Assistant Voice Preview hardware and compatible variants).

## Responsibilities

- Local wake word detection to avoid sending continuous audio over the network.
- Audio capture and streaming to the central assistant node.
- LED/sound feedback states for visual and audio acknowledgement.
- Receiving and acting on playback commands from the assistant core.

## Boundaries

**In scope:**
- Wake word detection engine integration.
- Audio streaming and buffering.
- Satellite-to-core protocol implementation.
- Device identity and diagnostics metadata.

**Out of scope:**
- ASR (speech-to-text) processing — handled by the assistant core.
- Dialogue management or response generation.

## Key Interfaces

- **Wake event → core**: emits a wake event with device ID and timestamp when the wake word is detected.
- **Audio stream → core**: streams audio frames or partial transcripts to the central node.
- **Playback command ← core**: receives TTS audio or interrupt signals from the central node.

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet implemented. See `docs/design/` for design notes and [docs/discussions/unresolved-items-and-open-questions.md](../../docs/discussions/unresolved-items-and-open-questions.md) for open questions.
