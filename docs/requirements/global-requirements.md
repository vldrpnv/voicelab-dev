# Global Requirements

## Purpose

This document captures high-level, cross-cutting requirements for the VoiceLab platform. These requirements apply to all components unless a component-local ADR explicitly documents an approved exception.

## Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-001 | The assistant must accept voice input streamed from Home Assistant Voice Preview hardware. | High |
| FR-002 | The assistant must route requests by complexity, urgency, privacy sensitivity, and capability. | High |
| FR-003 | The assistant must produce interruptible streaming TTS responses with low latency. | High |
| FR-004 | The assistant must acknowledge long-running requests with an interim spoken acknowledgement within 500ms. | High |
| FR-005 | Short local responses must complete within 2 seconds under normal conditions. | High |
| FR-006 | The assistant must support multi-step tool and workflow execution with state tracking. | Medium |
| FR-007 | The assistant must support multiple users with separate profiles, preferences, and state. | High |
| FR-008 | The assistant must answer broad open-ended questions with high quality, explicit uncertainty, and clarification when intent is ambiguous. | High |
| FR-009 | The assistant must gracefully degrade when external services are unavailable, offering cached or partial results. | High |
| FR-010 | The assistant must never expose raw API or infrastructure errors as user-facing speech output. | High |
| FR-011 | Spoken output must be sanitized to remove Markdown, code fences, URLs, and other TTS-unsafe formatting. | High |

## Non-Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| NFR-001 | All pipeline stages must produce structured logs with trace IDs and timestamps. | High |
| NFR-002 | Architecture must be modular; replacing a provider should not require a full rewrite. | High |
| NFR-003 | The system must run as a local-first service on a Mac mini. | High |
| NFR-004 | The system must be Linux-compatible in the near term. | High |
| NFR-005 | Optional Docker deployment must be supported. | Medium |
| NFR-006 | Development and CI must not require physical hardware. | High |
| NFR-007 | Secrets must never be committed to the repository. | High |
| NFR-008 | Remote LLM usage must remain below $50/month. | High |
