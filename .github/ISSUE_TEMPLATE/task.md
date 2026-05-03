---
name: Task
about: Issue template for agent/human tasks
title: ""
labels: ""
assignees: ""
---

## Goal

Describe the concrete outcome.

## Background

Short context. Do not include unnecessary global history.

## Relevant documents

- `docs/requirements/...`
- `docs/adr/...`
- `services/.../docs/adr/...`

## Allowed files / areas

- List the component directories or files this task is limited to.

## Out of scope

- Do not modify components not listed above.
- Do not introduce new providers or dependencies without an ADR.

## Required behavior

Describe expected behavior.

## Acceptance criteria

- [ ] Test exists and fails before implementation where practical.
- [ ] Implementation passes the test.
- [ ] Existing tests still pass.
- [ ] Logs or traces are updated if behavior affects the runtime pipeline.
- [ ] Relevant docs/ADR/specs are updated if behavior changed.
- [ ] No secrets or local paths are introduced.

## Test command

```
# Command to run relevant tests
```

## Notes for coding agents

- Keep the diff small.
- Do not refactor unrelated files.
- If the requirement is ambiguous, update the spec or stop for a decision.
