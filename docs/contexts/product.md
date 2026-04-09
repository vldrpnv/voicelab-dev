Problem:
- Current situation: Always-on Mac mini plus HomeAssistant Voice Preview hardware; current software (Home Assistant conversation) is slow, non-interruptible and underutilizes available HW.
- Pain: Slow ASR/TTS, long generation latencies, no interrupt/cut-in support, and brittle multi-tool orchestration make voice interactions feel unnatural and unusable for longer or complex tasks.
- Why alternatives fail: Existing voice/conversation engines target phone/call flows and batch-oriented LLM use; they lack low-latency streaming ASR->LLM->TTS pipelines, router-based model dispatch, and robust state transitions required for device/satellite orchestration.

Trigger moment:
- Frustration with slow, non-interruptible voice interactions and desire to harness local HW for low-latency, interruptible conversational control of devices and external "satellites."

Target user:
- Home automation power-users, integrators, and researchers who self-host and need low-latency voice agents to orchestrate devices and external services.

User maturity:
- Technical; comfortable with self-hosting, Home Assistant, macOS/Linux servers, and deploying local ML models or connecting to remote LLMs.

Core workflow:
1. Continuous/streaming ASR ingests audio and pushes partial transcripts to a router model.
2. Router decides: quick response locally, stream to an LLM, or forward to a satellite/tool; may emit an immediate "thinking/processing" acknowledgement.
3. Chosen model/tool generates streaming text that is turned into interruptible TTS while orchestrating device/satellite actions and maintaining conversation state.

Primary output:
- A local-first, latency-optimized conversational agent providing streaming ASR, router-based dispatch, interruptible streaming TTS, and device/satellite orchestration.

First release scope:
- Streaming ASR ingestion and partial-text forwarding; simple router model with local/remote dispatch rules; integration with Home Assistant and a satellite proxy; interruptible TTS with low-latency playback.

Non-goals:
- Not a cloud-managed, multi-tenant assistant on first release.
- Not a full general-purpose chat UI or phone-call oriented system.

Differentiator:
- Designed for low-latency streaming interaction, partial-response/acknowledgement UX, router-model dispatch that redirects heavy work to specialized models or satellites, and guaranteed interruptible TTS and stable state transitions.

Constraints:
- Target hardware: mac mini (always-on) and HomeAssistant Voice Preview devices.
- Prefer local-first processing for privacy and latency; LLM compute may be limited, so routing to satellites or remote models is required.

Must be true:
- A user can hold a natural, low-latency spoken conversation with the system.
- without experiencing multi-second TTS/response stalls or inability to interrupt.
- and can verify device/satellite actions and see a stable conversation state that recovers to a sensible default.

One-sentence product statement:
- A local-first, latency-optimized conversational agent that streams speech recognition into a router-driven LLM pipeline, supports interruptible streaming TTS, and orchestrates connected devices and satellites for complex tasks.