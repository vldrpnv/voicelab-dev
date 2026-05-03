# ADR conventions

## Naming
- Use `0001-short-title.md` (zero-padded numeric id).

## Minimum header
- Title
- Status
- Date
- Context
- Decision
- Consequences
- Related ADRs (optional)

## When ADR is required
- Non-trivial tradeoffs.
- Cross-context architectural impact.
- Changes that significantly alter runtime/operational behavior.

## Maintenance
- Update `ADR-INDEX.md` whenever ADR status/content changes.
- Mark replaced decisions as `superseded` and link the replacement.
