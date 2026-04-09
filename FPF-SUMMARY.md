# FPF summary for this repo

## Core rules
- Work inside one bounded context at a time.
- Separate facts, assumptions, decisions, and open questions.
- Prefer explicit interfaces between contexts.
- Every non-trivial change updates either a task note or a decision record.
- Publish outcomes in a view suitable for humans: code diff, task update, or decision note.

## Working loop
1. Identify context.
2. State goal and constraints.
3. Propose minimal change.
4. Validate.
5. Record decision if tradeoff was involved.
6. Publish concise result. 