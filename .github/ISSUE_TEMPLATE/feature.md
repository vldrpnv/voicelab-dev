---
name: Feature
about: New capability or behavior change
title: ""
labels: "type:feature"
assignees: ""
---

## Goal

Describe the concrete outcome.

## Background

Short context. Reference relevant docs, not global history.

## Relevant documents

- `docs/adr/...`
- `docs/mvp-slice.md`
- `services/.../README.md`

## Allowed files / areas

List the components or files this issue is allowed to change.

## Out of scope

- What must not be changed.
- What is deferred to a later milestone.

## Required behavior

Describe the expected behavior after this change.

## Acceptance criteria

- [ ] Test exists and fails before implementation where practical.
- [ ] Implementation passes the test.
- [ ] Existing tests still pass.
- [ ] Logs/traces updated if pipeline behavior changed.
- [ ] Relevant docs/ADRs updated if behavior changed.
- [ ] No secrets or local paths introduced.

## Test command

```
# Command to run the relevant tests
```

## Agent execution

`safe` / `human review required` / `not safe`
