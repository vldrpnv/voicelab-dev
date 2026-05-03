# Context catalogue

Purpose: map context indexes so agents can load indexes first and avoid unnecessary files.

## Index map
- Domains: `docs/context/domains/DOMAIN-INDEX.md`
- APIs: `docs/context/apis/API-INDEX.md`
- Data: `docs/context/data/DATA-INDEX.md`
- Runbooks: `docs/context/runbooks/RUNBOOK-INDEX.md`
- Testing: `docs/context/testing/TEST-INDEX.md`
- Architecture decisions: `docs/adr/ADR-INDEX.md`

## Rule
- Read only the indexes required for the active task.
- From each index, open only the specific target docs needed.

## Current state summary
- Domain context docs currently live in `docs/contexts/`.
- Requirements and MVP specs currently serve as API/data/testing references.
- Operational docs are currently CI/workflow-oriented; dedicated runbooks are not yet present.
