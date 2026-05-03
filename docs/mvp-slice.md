# MVP Slice — M0: Walking Skeleton

## Goal

Build the smallest useful technical path that proves the system architecture works end-to-end, without any real hardware, real providers, or real external services.

## Target Pipeline

```
simulated text request
  → assistant-core entry point
  → rule-based router stub
  → fake executor / response generator
  → spoken-output sanitizer
  → JSONL trace log with trace ID and timestamps
  → text output (no real TTS)
```

## In Scope

- Simulated text request input (no audio, no satellite)
- Simple assistant-core entry point
- Simple rule-based router (at least two paths)
- Fake executor returning test responses
- Spoken-output sanitizer (strips Markdown, converts artifacts to natural language)
- Trace ID assigned to every request
- Timestamped JSONL log entries for each pipeline stage
- CLI command to run one simulated interaction
- Unit tests for all components
- Golden tests for sanitizer output
- CI workflow running tests and secret scan

## Out of Scope

- Real satellite or wake word hardware
- Real ASR (speech-to-text)
- Real TTS (text-to-speech) playback
- Real Home Assistant device control
- Real LLM API calls
- Multi-user profiles or voice recognition
- Deployment automation
- Long-term memory or persistence
- Cloud/local model benchmarking
- Firmware development
- Custom wake word training

## Success Criteria

| Criterion | Required Result |
|---|---|
| Simulated input exists | A test or CLI can submit a simulated text request |
| Router exists | The request is classified by a simple rule-based router |
| Fake executor exists | At least one fake response is produced |
| Sanitizer exists | Markdown or technical artifacts are converted to spoken-safe text |
| Trace exists | Every request gets a trace ID and timestamped pipeline events |
| Tests exist | Main components have unit tests |
| CI exists | GitHub Actions runs tests and secret scan without hardware |
| Docs exist | Architecture and process decisions are documented |

## Hardware Independence

All M0 work must run on a standard laptop or cloud CI runner. No real hardware, no local device paths, no API credentials required.

See [ADR-0003](adr/0003-hardware-independent-development.md).

## Next Step After M0

Once the walking skeleton is stable and CI is green, replace one fake layer at a time with a real implementation, starting with the spoken-output sanitizer (most testable) and TTS output path.
