# Architecture Context

## System context
A local executive-assistant orchestration server on an always-on mac mini that ingests streaming audio from HomeAssistant devices, routes partial transcripts through intent/complexity decisioning, and orchestrates local/remote models and tools for high-quality, interruptible responses and dependable action execution.

## Architectural goals
- Low latency
- High response quality for broad questions
- Privacy / local-first
- Modularity and clear module boundaries
- Observability for debugging and telemetry

## Major modules
### ASR Ingestor
- Responsibility: Capture streaming audio from HA devices and emit partial transcripts with timestamps and confidence.
- Inputs: Audio stream from HomeAssistant devices.
- Outputs: Partial transcripts, timestamps, confidences.
- Depends on: Audio drivers / HA integration.

### Router
- Responsibility: Classify partials and decide dispatch target (local model, remote LLM, satellite) with priority and timeout hints.
- Inputs: ASR partial stream, session context, router policy.
- Outputs: Dispatch decision, priority flag, target and timeout.
- Depends on: Router policy configuration, session state.

### Quality Layer
- Responsibility: Enforce answer-quality behaviors (uncertainty signaling, clarification prompts, completeness checks) before and during response delivery.
- Inputs: Draft responses, tool outputs, session context, quality policy.
- Outputs: Quality annotations, clarification requests, safe/uncertain response markers.
- Depends on: Quality policy, confidence heuristics, optional verifier/evaluator adapters.

### Dispatcher / Orchestrator
- Responsibility: Forward requests to chosen models or satellites, manage callbacks, merge streaming outputs, and coordinate TTS playback.
- Inputs: Router decisions, session context.
- Outputs: Streaming text payloads, action commands for devices, playback metadata.
- Depends on: Local/remote model adapters, satellite proxies, quality layer, TTS player.

### TTS Player
- Responsibility: Convert streaming text to interruptible audio playback, manage audio output and cut-ins.
- Inputs: Streaming text with interrupt flags and voice metadata.
- Outputs: Audio playback, interrupt events.
- Depends on: Local TTS engine or remote TTS API, audio output device.

## Data model / core artifacts
- Conversation session/state (active tool, history, timeouts)
- Router policy and decision logs
- Quality policy and quality-event logs (uncertainty/clarification/verification events)
- Short-term audio buffers for active sessions

## Key flows
1. Streaming ASR -> Router -> Dispatcher -> TTS playback (with interrupts).
2. Router-led satellite dispatch with interim ACK and result callback.
3. Quality-gated response flow: draft answer/tool result -> quality layer -> stream response with uncertainty/clarification when needed.
4. State management: detect satellite/tool timeout and revert to default.

## Boundaries and interfaces
- ASR -> Router: partial transcript stream with timestamps and confidence.
- Router -> Dispatcher: dispatch decision, priority flag, optional tool target and expected timeout.
- Dispatcher/Model -> Quality Layer: draft answer chunks, tool evidence, confidence signals.
- Quality Layer -> TTS/Client: approved chunks with quality annotations (clarify/uncertain/verified).
- Dispatcher -> TTS Player: streaming text + interrupt flag and metadata (voice, ssml).

## External integrations
- Home Assistant and Voice Preview hardware
- Remote LLM APIs and satellite services
- Local TTS engines (Coqui, Edge TTS) and optional remote TTS
- External telemetry/logging service for structured logs

## State and storage
- Conversation sessions stored in a lightweight local DB (sqlite).
- Router decision logs and telemetry sent to an external logging/telemetry service.
- Short-term audio buffers held in memory and rotated out.

## Deployment assumptions
- Local-first service on a mac mini with optional Docker deployment; near-term Linux compatibility is required; satellites are optional external services.

## Operational concerns
- Structured logs and telemetry to external service for debugging and metrics.
- Health checks and timeouts for satellites and model adapters.
- Replayable session traces (audio + transcripts) for debugging.
- Track quality KPIs (helpfulness, factuality proxy, clarification rate, task completion success).

## Security / privacy assumptions
- Local-first; remote models used only when explicitly configured; secrets stored encrypted locally.

## Open architectural questions
- Router policy: rule-based heuristics vs learned policy and how to safely update it.
- TTS interrupt mechanism choices and required engine support.
- Persistence strategy for conversation state vs ephemeral-only trade-offs.
- Multi-user profile isolation model (separate user configs, model preferences, and policy boundaries).
- Which quality checks must be synchronous in the response path versus asynchronous post-response evaluation.
