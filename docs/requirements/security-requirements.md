# Security Requirements

## Purpose

This document specifies security and privacy requirements for the VoiceLab platform.

## Data and Privacy

| ID | Requirement | Priority |
|---|---|---|
| SEC-001 | Raw audio must not be stored long-term by default. Only short-term buffers for active sessions are allowed. | High |
| SEC-002 | Session metadata and transcripts must be stored locally in SQLite. | High |
| SEC-003 | Logs must not become a privacy liability; apply redaction and retention policies. | High |
| SEC-004 | Default retention duration for transcript logs must be defined and enforced. | High |
| SEC-005 | Raw audio capture must be opt-in only. | High |
| SEC-006 | Remote LLMs must only be used when explicitly configured by the user or operator. | High |

## Secrets and Credentials

| ID | Requirement | Priority |
|---|---|---|
| SEC-007 | No secrets, API keys, tokens, passwords, or private hostnames must ever be committed to the repository. | High |
| SEC-008 | Secrets must be stored encrypted locally and never exported. | High |
| SEC-009 | Configuration templates must use placeholder values, not real credentials. | High |
| SEC-010 | CI must include secret scanning on every push and pull request. | High |

## Access Control

| ID | Requirement | Priority |
|---|---|---|
| SEC-011 | Multi-user operation must include per-user isolation: separate config, history, and runtime quotas. | High |
| SEC-012 | The per-user isolation boundary must be defined before user profile features are implemented. | High |
| SEC-013 | Identity confidence required before accessing private user context must be specified. | Medium |

## Open Questions

- What is the minimum identity confidence threshold before the assistant uses a user's private context?
- What is the default and maximum transcript retention duration?
- Which transcript fields are subject to mandatory redaction in logs?
