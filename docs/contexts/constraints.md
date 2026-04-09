

# Constraints Context

## Purpose of this document
<!-- Capture the hard constraints, preferred constraints, and explicit tradeoffs that shape product and architecture decisions. -->

## Non-negotiable constraints
<!-- Constraints that must hold from day one. -->

- Local-first processing by default; remote models are used only when explicitly configured.
- Strict latency targets: interim ACK in <500ms and short replies in <2s under normal conditions.
- Interruptible TTS behavior is required to support natural cut-ins.
- Assistant must maintain a high quality bar for broad question answering: clear responses, explicit uncertainty, and clarification requests when intent is ambiguous.

## Strong preferences
<!-- Important constraints that guide decisions, but may be relaxed with justification. -->

- Use sqlite for conversation session/state persistence.
- Start with a rule-based router policy before introducing learned policies.
- Prefer local TTS engines first (Coqui/Edge/local alternatives), with remote providers as optional.

## Cost constraints
<!-- Budget, token usage, hosting, tooling, maintenance effort. -->

- Remote LLM usage budget target: < $50/month.
- Prefer routing to local paths whenever quality/latency constraints are still met.

## Technical constraints
<!-- Language, runtime, platform, repo shape, deployment model, performance limits. -->

- Must run as an always-on local-first service on mac mini.
- Optional Docker/container deployment is supported.
- Near-term Linux compatibility is a requirement.
- Must integrate with Home Assistant Voice Preview hardware.

## Product constraints
<!-- Scope limits, target audience limits, UX limits, release limits. -->

- Multi-user operation is required, including per-user configuration for LLM/TTS.
- Phone-calling/telephony workflows are out of scope.
- UX must prioritize conversational naturalness (streaming + interruption).
- System scope explicitly includes full-scale executive-assistant behavior: answering broad user questions and executing multi-step tasks across connected tools/services.

## Data and privacy constraints
<!-- What data may be stored, what must stay local, what may leave the machine, retention expectations. -->

- Store session metadata and transcripts locally in sqlite.
- Do not store raw audio long-term by default.
- Keep secrets encrypted locally and never export them.

## Operational constraints
<!-- Logging, reproducibility, testability, support burden, observability, change management. -->

- Use structured telemetry/logging externally for observability and debugging.
- Maintain timeout and fallback behavior for satellites/providers to preserve stable UX.
- Keep architecture modular to enable provider replacement without full rewrites.
- Track and review quality KPIs (e.g., user-rated helpfulness, factuality proxy, clarification effectiveness, and task completion rate).

## Agent workflow constraints
<!-- Constraints specific to Roo Code, git workflows, prompts, file-based memory, command usage, etc. -->

- Keep changes small and traceable in context docs; update architecture/context files before implementation details.
- Prefer bounded-context updates and explicit tradeoff recording.

## External dependency constraints
<!-- Which vendors, providers, protocols, or ecosystems are required, optional, or to be avoided. -->

- Required: Home Assistant ecosystem integration.
- Optional: remote LLM APIs and TTS providers.
- Avoid vendor lock-in by keeping adapters pluggable across providers.

## Explicit tradeoffs accepted
<!-- What you are willing to sacrifice in order to satisfy the important constraints. -->

- Accept occasional response-quality drop on local fallback to keep latency targets.
- Accept higher implementation complexity to achieve interruptible streaming UX.
- Accept added orchestration/validation overhead to sustain "respond WELL" quality expectations.

## Explicit tradeoffs rejected
<!-- Tempting directions that should be avoided because they violate the desired operating model. -->

- Reject adding phone-call/telephony workflows.
- Reject tight coupling to a single LLM/TTS vendor.

## Open questions
<!-- Unresolved constraints or tensions that still need decisions. -->

- Policy for multi-user isolation boundaries (config, history, and runtime quotas).
- Whether transcript retention should be configurable by user/profile and for how long.
- Which minimum quality thresholds should gate production rollout for executive-assistant capabilities.
