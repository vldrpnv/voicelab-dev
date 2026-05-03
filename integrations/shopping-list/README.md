# Shopping List Integration

## Purpose

Adapter for managing a shared household shopping list, used by the assistant core for shopping list queries and updates.

## Responsibilities

- Add, remove, and query items on the shopping list.
- Persist the list locally (SQLite or equivalent).
- Support snapshot caching for offline fallback.
- Provide a stub/fake implementation for hardware-independent testing.

## Boundaries

**In scope:**
- Shopping list CRUD operations.
- Local persistence and snapshot caching.

**Out of scope:**
- Shopping list display or spoken formatting (assistant core responsibility).
- Multi-user list sharing or sync (may be added later).

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet implemented. See `docs/design/` for design notes.
