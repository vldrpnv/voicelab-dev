---
name: Bug
about: Incorrect or unexpected behavior
title: ""
labels: "type:bug"
assignees: ""
---

## What Happened

Describe the actual behavior.

## What Was Expected

Describe the correct behavior.

## Steps to Reproduce

1. ...
2. ...
3. ...

## Relevant logs or traces

Paste a trace ID, JSONL log snippet, or test output if available.

## Environment

- Component: (e.g., `services/router`, `services/tts-output`)
- How was it discovered: (test failure / manual run / CI failure)

## Out of scope

- Do not fix unrelated issues in the same PR.

## Acceptance criteria

- [ ] A failing test reproduces the bug.
- [ ] The fix makes the test pass.
- [ ] Existing tests still pass.
- [ ] Root cause is noted in the PR description.

## Test command

```
# Command to run the relevant tests
```

## Agent execution

`safe` if the bug is well-scoped and reproducible by test. `human review required` if root cause is unclear.
