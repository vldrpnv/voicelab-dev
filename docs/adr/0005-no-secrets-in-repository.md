# ADR-0005: No Secrets in Repository

## Status

Accepted

## Context

The repository may be shared with external contributors and coding agents. Committing secrets (API keys, tokens, passwords, private hostnames, local credentials) creates a security and privacy risk even in a private repository. Once committed, a secret is hard to fully revoke even after removal from history.

## Decision

No secrets, tokens, API keys, private hostnames, or local credentials are ever committed to this repository.

Enforcement:
- CI secret scanning runs on every push and pull request (see `.github/workflows/secret-scan.yml`).
- Secret scanning must fail if obvious secret patterns are detected.
- Configuration requiring secrets uses environment variables or a local `.env` file listed in `.gitignore`.
- Example and template config files use placeholder values (e.g., `YOUR_API_KEY_HERE`).
- Deployment scripts source secrets from the local environment, not from repository files.

Allowed in the repository:
- Placeholder values clearly marked as examples.
- Public service URLs and non-sensitive configuration defaults.
- Documentation describing which secrets are needed and how to configure them locally.

## Consequences

- Developers manage secrets locally; CI enforces the no-commit rule automatically.
- Coding agents cannot accidentally commit credentials found in the workspace.
- All contributors work under the same secret hygiene baseline.
