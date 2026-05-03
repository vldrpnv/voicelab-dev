# VoiceLab Roadmap

## Core Idea: Walking Skeleton First

Do not start with the full assistant. Start with a walking skeleton — a tiny end-to-end version of the system that proves the shape of the architecture without solving the hard parts yet.

The first meaningful goal is:

> Simulated satellite input → assistant core → router → fake executor → TTS-safe output → trace log.

That gives a stable foundation for planning, testing, and future agent-assisted development.

---

## Workstreams

| Workstream | Purpose | Status |
|---|---|---|
| `docs-process` | Repository structure, ADRs, issue templates, planning rules | **Active** |
| `walking-skeleton` | Minimal end-to-end assistant loop with fake inputs/outputs | **Active — M0** |
| `observability` | Trace IDs, timestamps, logs, replayable traces | **Active — M0** |
| `tts-output` | Convert assistant output into spoken-safe text | **Active — M0** |
| `router` | Decide what should handle a request | **Active — M0 (simple only)** |
| `satellite-firmware` | Firmware changes, wake events, audio streaming | Later |
| `wakeword-training` | Custom wake word dataset/model/evaluation | Parallel — separate project |
| `home-assistant-integration` | Real HA device/service integration | Later (fake adapter first) |
| `deployment` | Private-network auto-deploy | Later |
| `multi-user` | Voice recognition, profiles, permissions | Later |

---

## Milestones

### M0 — Walking Skeleton

**Goal:** Build the smallest useful technical path.

```
simulated request
  → assistant-core
  → router
  → fake executor
  → spoken-output sanitizer
  → trace log
  → text output
```

**Scope:** See [mvp-slice.md](mvp-slice.md) and [docs/mvp/m0-walking-skeleton.md](mvp/m0-walking-skeleton.md).

**Out of scope for M0:**
- Real satellite firmware
- Real wake word
- Real Home Assistant device control
- Real cloud/local provider orchestration
- Real TTS playback
- Multi-user support
- Deployment automation

### M1 — Real Integrations (planned)

Replace fake components with real ones, one at a time:
- Real TTS output path with sanitizer validation
- Real Home Assistant adapter (fake still available for CI)
- Real router policy with at least two tested dispatch paths
- Structured trace export to external log store

### M2 — Satellite and Wake Word (planned)

- Home Assistant Voice Preview satellite integration
- Custom wake word training project started
- Real ASR pipeline from satellite audio

---

## Decision Rule for New Ideas

| Category | Meaning | Action |
|---|---|---|
| `Now` | Needed for M0 walking skeleton | Add to current milestone |
| `Soon` | Needed after skeleton works | Add to next milestone |
| `Parallel` | Separate workstream, not blocking skeleton | Create separate milestone |
| `Later` | Valuable but not needed soon | Add to backlog |
| `Research` | Unknown feasibility | Create spike issue |
| `Reject for now` | Too distracting or premature | Record in discussion notes only |

### Examples

| Idea | Category |
|---|---|
| Simulated request input | Now |
| Trace IDs | Now |
| TTS sanitizer | Now |
| Real Home Assistant control | Soon |
| Custom wake word training | Parallel |
| Firmware modification | Parallel/Soon |
| Multi-user voice recognition | Later |
| Automatic private deploy | Later |
| Real cloud/local model benchmark | Soon/Research |
