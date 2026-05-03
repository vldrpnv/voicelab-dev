# Issue Planning Rules

Every issue should be small enough that a human or coding agent can complete it without inventing architecture.

---

## Rule 1: One issue changes one thing

**Good:**
```
Add trace ID generation to assistant-core.
```

**Bad:**
```
Implement the assistant.
```

---

## Rule 2: Every issue must state what is out of scope

Example:
```
Out of scope:
- Do not implement real TTS.
- Do not call any LLM API.
- Do not modify firmware.
- Do not introduce database persistence yet.
```

---

## Rule 3: Every issue must include acceptance criteria

Example:
```
Acceptance criteria:
- Given a fake request, a trace ID is created.
- The trace ID appears in all pipeline log events.
- Unit tests cover trace ID creation.
- Existing tests pass.
```

---

## Rule 4: Every implementation issue must name relevant docs

Example:
```
Relevant docs:
- docs/mvp-slice.md
- docs/adr/0002-walking-skeleton-first.md
- services/assistant-core/README.md
```

---

## Rule 5: Every issue must say whether it is agent-safe

Use this field:
```
Agent execution: safe / not safe / human review required
```

| Value | Meaning |
|---|---|
| `safe` | Small, well-scoped; tests define the expected result; no architectural decision needed |
| `human review required` | Agent can draft, but a human must inspect the design impact before merging |
| `not safe` | Requires product or design judgment before any coding begins |

---

## Issue Planning Checklist

Before creating any issue, answer these questions:

| Question | Why it matters |
|---|---|
| What is the smallest useful result? | Prevents oversized issues |
| Which component owns this? | Prevents cross-component drift |
| Which docs are relevant? | Keeps design-first flow |
| What is explicitly out of scope? | Prevents uncontrolled expansion |
| How will this be tested without hardware? | Keeps development hardware-independent |
| What logs/traces should this produce? | Preserves debuggability |
| What can fail, and what is the fallback? | Forces fallback thinking |
| Can a coding agent safely do this? | Determines task shape |
| What must not be changed? | Prevents agent overreach |
| What is the definition of done? | Avoids vague completion |

---

## Issue Template Structure

Every implementation issue should follow this structure:

```markdown
# Task

## Goal
Describe the concrete outcome.

## Background
Short context. Do not include unnecessary global history.

## Relevant documents
- docs/...
- services/.../README.md

## Allowed files / areas
List what this issue is allowed to change.

## Out of scope
List what must not be changed.

## Required behavior
Describe expected behavior.

## Acceptance criteria
- [ ] Test exists and fails before implementation.
- [ ] Implementation passes the test.
- [ ] Existing tests still pass.
- [ ] Docs updated if behavior changed.
- [ ] No secrets or local paths introduced.

## Test command
Command to run the relevant tests.

## Agent execution
safe / human review required / not safe
```

---

## Labels Reference

| Label | Meaning |
|---|---|
| `type:feature` | New capability |
| `type:bug` | Incorrect behavior |
| `type:spike` | Research / investigation |
| `type:adr` | Architecture decision needed |
| `type:docs` | Documentation-only work |
| `type:test` | Test infrastructure or coverage |
| `type:infra` | CI, deployment, repo tooling |
| `area:assistant-core` | Core assistant loop |
| `area:router` | Routing logic |
| `area:tts-output` | Spoken output formatting/sanitizing |
| `area:observability` | Logs, traces, metrics |
| `area:satellite` | Satellite/firmware concerns |
| `area:wakeword` | Wake word training/evaluation |
| `area:ha-integration` | Home Assistant integration |
| `agent-safe` | Suitable for autonomous coding agent |
| `needs-human-decision` | Requires design/product decision first |
| `blocked` | Cannot proceed yet |
