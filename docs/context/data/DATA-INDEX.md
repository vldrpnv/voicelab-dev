# Data index

Purpose: catalog data models, schema decisions, and migration references.

## When to load
- Schema/model changes
- Migration planning
- Persistence behavior questions

## Entries
| Data area | Canonical docs | Migration refs | Backward-compat notes | Last reviewed |
|---|---|---|---|---|
| Session/transcript storage requirements | [`docs/requirements/security-requirements.md`](../../requirements/security-requirements.md), [`docs/contexts/constraints.md`](../../contexts/constraints.md), [`docs/contexts/architecture.md`](../../contexts/architecture.md) | No migrations yet | SQLite and retention policy are required but still pre-implementation | 2026-05-03 |
| Pipeline traces and telemetry | [`docs/requirements/observability-requirements.md`](../../requirements/observability-requirements.md), [`docs/mvp-slice.md`](../../mvp-slice.md), [`docs/mvp/m0-walking-skeleton.md`](../../mvp/m0-walking-skeleton.md) | No migrations yet | Trace schema is still evolving during M0 | 2026-05-03 |
