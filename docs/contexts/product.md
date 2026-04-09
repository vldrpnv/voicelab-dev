Problem:
- Current situation: Always-on Mac mini plus HomeAssistant Voice Preview hardware; current software is optimized for basic commands, not full executive-assistant behavior.
- Pain: The system handles short interactions but does not yet provide consistently high-quality answers for open-ended, cross-domain questions or reliable end-to-end task execution.
- Why alternatives fail: Typical voice stacks optimize either latency or answer quality, but not both; they often lack robust routing, tool orchestration, and quality controls needed for an executive assistant that must answer broadly and well.

Trigger moment:
- Need to evolve from a fast home-automation voice interface into a full-scale executive assistant that can answer any question with strong quality and execute complex tasks across tools/services.

Target user:
- Power users, operators, founders/executives, and researchers who need a local-first assistant that can handle broad questioning, planning, and execution while preserving low-latency conversational UX.

User maturity:
- Technical; comfortable with self-hosting, Home Assistant, macOS/Linux servers, and deploying local ML models or connecting to remote LLMs.

Core workflow:
1. Continuous/streaming ASR ingests audio and pushes partial transcripts to a router model.
2. Router classifies intent/question complexity, chooses local/remote/tool paths, and emits immediate acknowledgement when needed.
3. Assistant composes an answer using retrieval/reasoning/tool outputs, executes requested actions, and returns a streaming, interruptible response.
4. Quality layer checks answer quality (correctness/completeness/clarity/uncertainty signaling) before or during delivery.

Primary output:
- A local-first, full-scale executive assistant that responds well to broad user questions and executes multi-step tasks through reliable orchestration, while preserving low-latency interruptible conversation.

First release scope:
- Streaming ASR ingestion and partial-text forwarding.
- Router model with local/remote/tool dispatch rules for both simple commands and open-ended questions.
- Answer-quality baseline: explicit uncertainty handling, clarification prompts for ambiguity, and concise structured responses for factual/operational queries.
- Integration with Home Assistant and a satellite/tool proxy; interruptible TTS with low-latency playback.

Non-goals:
- Not a cloud-managed, multi-tenant assistant on first release.
- Not a phone-call oriented system.

Differentiator:
- Combines low-latency streaming interaction with a high answer-quality bar for broad question answering, plus router-based orchestration for specialized tools/satellites and guaranteed interruptible TTS.

Constraints:
- Target hardware: mac mini (always-on) and HomeAssistant Voice Preview devices.
- Prefer local-first processing for privacy and latency; LLM compute may be limited, so routing to satellites or remote models is required.

Must be true:
- A user can ask broad, open-ended questions and receive high-quality answers that are clear, relevant, and explicit about uncertainty.
- A user can hold a natural, low-latency spoken conversation without multi-second stalls or inability to interrupt.
- A user can request multi-step actions and verify outcomes through stable conversation/tool state that recovers to a sensible default.

One-sentence product statement:
- A local-first, latency-optimized executive assistant that answers broad user questions well, streams speech recognition into a router-driven reasoning/execution pipeline, supports interruptible TTS, and orchestrates connected devices and satellites for complex tasks.
