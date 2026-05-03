# ADR-0004: No Secrets in Repository

## Status

Accepted

## Context

The repository may be shared with external contributors and coding agents. Committing secrets (API keys, tokens, passwords, private hostnames, local credentials) would create a security and privacy risk even in a private repository.

## Decision

No secrets, tokens, API keys, private hostnames, or local credentials are ever committed to this repository.

Enforcement mechanisms:
- CI secret scanning runs on every push and pull request (see `.github/workflows/secret-scan.yml`).
- Secret scanning must fail if obvious test secret patterns are detected.
- Configuration that requires secrets uses environment variables or a local `.env` file that is listed in `.gitignore`.
- Example or template config files use placeholder values (e.g., `YOUR_API_KEY_HERE`).

## Consequences

- Developers must manage secrets locally and not rely on committing them for convenience.
- CI will catch accidental commits before they merge.
- Example configs must be clearly marked as templates.
- Deployment scripts must source secrets from the local environment, not from repository files.
