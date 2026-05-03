# Voice UX Requirements

## Purpose

This document specifies voice user experience requirements for the VoiceLab assistant. These requirements govern how the assistant listens, responds, and behaves during spoken interactions.

## Listening and Input

| ID | Requirement | Priority |
|---|---|---|
| VUX-001 | The assistant must not interrupt too aggressively while the user is still formulating a request. | High |
| VUX-002 | VAD (Voice Activity Detection) endpointing must tolerate slow speakers and natural pauses. | High |
| VUX-003 | The assistant should support a configurable "wait longer" behavior per user or profile. | Medium |
| VUX-004 | Wake word detection must happen on the satellite device to reduce network load. | High |

## Response Behavior

| ID | Requirement | Priority |
|---|---|---|
| VUX-005 | Responses must be interruptible: the user must be able to cut in at any point. | High |
| VUX-006 | Interim acknowledgement ("I'm checking that") must be emitted within 500ms for longer tasks. | High |
| VUX-007 | Short conversational responses must feel natural, not robotic or template-driven. | High |
| VUX-008 | The assistant must support multi-turn context: subsequent requests may refer to previous responses. | High |
| VUX-009 | Clarification questions must be asked when user intent is ambiguous, not assumed. | High |
| VUX-010 | The assistant must explicitly signal uncertainty rather than stating incorrect information confidently. | High |

## Output Format

| ID | Requirement | Priority |
|---|---|---|
| VUX-011 | Spoken text must be separate from logged or display text; use distinct output channels. | High |
| VUX-012 | Markdown, code fences, table syntax, bullets, and raw URLs must be stripped or converted before TTS. | High |
| VUX-013 | Responses that would sound unnatural when spoken aloud must be reformatted for speech. | High |

## Personality and Tone

| ID | Requirement | Priority |
|---|---|---|
| VUX-014 | The assistant must have a defined, consistent personality: practical, clear, not theatrical. | Medium |
| VUX-015 | Spoken responses must be concise; avoid repeating context the user already provided. | High |
| VUX-016 | Failure messages must be brief and humanly phrased, not technical. | High |

## Open Questions

- What exact VAD parameters (silence duration, energy thresholds) are acceptable for the primary user?
- Should personality be global or configurable per user profile?
- Which child-related use cases are in scope and what age-aware response mode is required?
