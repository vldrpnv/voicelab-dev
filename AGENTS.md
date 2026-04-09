# Agent operating rules

## Goal
Implement changes with minimal token usage and high traceability.

## Method
- Use FPF-SUMMARY.md as the default reasoning scaffold.
- For heavy architectural tasks, use FPF-Spec.md.
- Read only the files necessary for the current task.
- Stay within one bounded context unless the task explicitly crosses boundaries.
- For non-trivial tradeoffs, update docs/decisions/.
- For implementation tasks, prefer small diffs and existing patterns.

## Output discipline
- Keep plans short.
- Do not restate repository-wide context unless necessary.
- Do not quote large documents back to the user.
- Summarize findings in bullets, then act.

## Validation
- Run tests/lint only for touched areas where possible.
- Report changed files, validation status, and open questions.