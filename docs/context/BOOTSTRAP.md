# Context bootstrap

Purpose: load minimal context first, then expand only as needed.

## Default load order
1. `AGENTS.md`
2. `FPF-SUMMARY.md` (or `FPF-Spec.md` for architecture-heavy work)
3. `docs/context/CATALOG.md`
4. Relevant index files only
5. Target docs referenced by those index files

## Task routing

### Bug fix
- Load: `domains/DOMAIN-INDEX.md`, `runbooks/RUNBOOK-INDEX.md`, `testing/TEST-INDEX.md`
- Then load only module/runbook/test docs for the touched area.

### Feature work
- Load: `domains/DOMAIN-INDEX.md`, `apis/API-INDEX.md`, `data/DATA-INDEX.md`, `testing/TEST-INDEX.md`
- Then load only affected contracts and acceptance docs.

### Refactor
- Load: `domains/DOMAIN-INDEX.md`, `testing/TEST-INDEX.md`
- Add `adr/ADR-INDEX.md` if behavior or architecture could change.

### Architecture change
- Load: `adr/ADR-INDEX.md`, `domains/DOMAIN-INDEX.md`, `apis/API-INDEX.md`, `data/DATA-INDEX.md`, `runbooks/RUNBOOK-INDEX.md`
- Create/update ADR and related docs in same change.

### Ops / incident
- Load: `runbooks/RUNBOOK-INDEX.md`, `domains/DOMAIN-INDEX.md`, `testing/TEST-INDEX.md`
- Update runbook + post-incident notes where relevant.
