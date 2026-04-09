# Domain Context

## One-sentence domain definition
Low-latency local-first conversational orchestration for home automation and external services (satellites).

## Primary users / actors
- Home automation power-users / tinkerers who self-host.
- Home Assistant runtime and device firmware (HomeAssistant Voice Preview HW).
- Remote LLMs, satellite services, and integrators that provide specialized capability.

## Core user goals
- Low-latency natural voice control of devices.
- Reliable orchestration of satellites and remote tools for heavy tasks.
- Predictable, interruptible streaming responses (TTS) and acknowledgements.

## Domain objects / entities
- ASR partials / transcripts
- Router model (decisioning)
- Satellites / external tools
- Conversation session / state

## Key workflows
1. Streaming ASR -> router -> dispatch -> interruptible TTS playback and device actions.
2. Router forwards heavy queries to satellite/remote LLM and emits interim "thinking" acknowledgement.
3. State management: detect satellite/tool timeouts or failures and revert to a stable default state.

## Boundaries
### In scope
- Local ASR/TTS pipelines, router decisioning, Home Assistant integration, satellite proxying and orchestration.

### Out of scope
- Cloud-hosted multi-tenant assistant or phone-call oriented call-center workflows.

## Rules and constraints
- Latency targets: sub-500ms for interim ACKs, sub-2s for short replies.
- Privacy: local-first processing unless user explicitly routes to remote models.
- Fallback: router must emit an interim acknowledgement and gracefully forward or retry on heavy queries.

## Data and state
- ASR partials and final transcripts
- Conversation sessions/state (active tool, timeouts, history)
- Router decisions, logs and telemetry

## External systems and integrations
- Home Assistant and device firmware
- Remote LLM APIs and satellite services
- Local TTS engines (Coqui, Edge TTS, etc.)

## Failure modes / edge cases
- Router misclassification leads to wrong dispatch and added latency.
- Satellite or remote LLM timeouts or slow responses; requires interim ACK and fallback.
- Non-interruptible TTS causing poor UX and inability to cut in.

## Open questions
- How to persist conversation state versus keeping it ephemeral only (trade-offs for privacy, debugging, and recovery).
