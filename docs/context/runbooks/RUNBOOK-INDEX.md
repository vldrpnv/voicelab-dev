# Runbook index

Purpose: catalog operational playbooks and troubleshooting guides.

## When to load
- Incidents and production issues
- Deployment/rollback procedures
- Operational maintenance tasks

## Entries
| Runbook | Trigger/Use case | Canonical docs | Escalation | Last reviewed |
|---|---|---|---|---|
| CI validation baseline | Verify branch health before merge | [`.github/workflows/ci.yml`](../../../.github/workflows/ci.yml), [`docs/development-process.md`](../../development-process.md) | Fix failing test setup first, then re-run CI | 2026-05-03 |
| Secret scanning baseline | Verify no secrets/tokens are committed | [`.github/workflows/secret-scan.yml`](../../../.github/workflows/secret-scan.yml), [`docs/adr/0005-no-secrets-in-repository.md`](../../adr/0005-no-secrets-in-repository.md) | Rotate/revoke and remove exposed credentials immediately | 2026-05-03 |
