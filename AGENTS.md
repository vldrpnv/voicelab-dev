# Agent operating rules

## Goal
Implement changes with minimal token usage and high traceability.

## Method
- Use FPF-SUMMARY.md as the default reasoning scaffold.
- For heavy architectural tasks, use FPF-Spec.md.
- Use bootstrap-loading to avoid overfilling context (see `docs/context/BOOTSTRAP.md`).
- Read only the files necessary for the current task.
- Stay within one bounded context unless the task explicitly crosses boundaries.
- For non-trivial tradeoffs, update architecture decisions (ADR) and related docs.
- For implementation tasks, prefer small diffs and existing patterns.

## Bootstrap loading (mandatory)
1. Load `AGENTS.md`.
2. Load `FPF-SUMMARY.md` (or `FPF-Spec.md` for architecture-heavy tasks).
3. Load `docs/context/BOOTSTRAP.md`.
4. Load only relevant index files first:
   - `docs/context/CATALOG.md`
   - `docs/adr/ADR-INDEX.md`
   - One or more of:
     - `docs/context/domains/DOMAIN-INDEX.md`
     - `docs/context/apis/API-INDEX.md`
     - `docs/context/data/DATA-INDEX.md`
     - `docs/context/runbooks/RUNBOOK-INDEX.md`
     - `docs/context/testing/TEST-INDEX.md`
5. Load only target documents referenced by those indexes for the current task.

## ADR catalogue usage (mandatory)
- Consult `docs/adr/ADR-INDEX.md` before architecture-affecting changes.
- If a decision is non-trivial or has cross-context impact, add/update an ADR.
- Keep ADR records concise and link superseded decisions.
- Update `docs/adr/ADR-INDEX.md` in the same change whenever ADRs change.

## Documentation sync policy (always-on)
- Always update relevant documentation in the same change when behavior, architecture, interfaces, operations, or tests are affected.
- Relevant docs may include:
  - ADRs (`docs/adr/`)
  - domain docs (`docs/context/domains/`)
  - API contracts (`docs/context/apis/`)
  - data contracts/migrations (`docs/context/data/`)
  - runbooks/ops notes (`docs/context/runbooks/`)
  - testing strategy/notes (`docs/context/testing/`)
- If no documentation updates are needed, explicitly state why in the task summary.

## Output discipline
- Keep plans short.
- Do not restate repository-wide context unless necessary.
- Do not quote large documents back to the user.
- Summarize findings in bullets, then act.

## Validation
- Run tests/lint only for touched areas where possible.
- Report changed files, validation status, and open questions.
