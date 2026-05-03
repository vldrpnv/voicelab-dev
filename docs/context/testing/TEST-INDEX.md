# Test index

Purpose: catalog testing strategy and area-specific test guidance.

## When to load
- Adding/changing tests
- Interpreting failures
- Determining minimal validation scope

## Entries
| Area | Test types | Commands/paths | Coverage notes | Last reviewed |
|---|---|---|---|---|
| Repository CI baseline | Python unit tests via pytest | `python -m pytest tests/ -v`, [`.github/workflows/ci.yml`](../../../.github/workflows/ci.yml) | `tests/test_placeholder.py` currently ensures collection while M0 tests are still planned | 2026-05-03 |
| MVP walking-skeleton acceptance | Unit + golden + end-to-end expectations (planned) | [`docs/mvp-slice.md`](../../mvp-slice.md), [`docs/mvp/m0-walking-skeleton.md`](../../mvp/m0-walking-skeleton.md), [`docs/mvp/acceptance-criteria.md`](../../mvp/acceptance-criteria.md) | Acceptance exists in docs; implementation coverage is pending | 2026-05-03 |
