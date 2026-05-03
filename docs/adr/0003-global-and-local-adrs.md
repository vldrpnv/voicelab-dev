# ADR-0003: Global and Component-Local Architectural Decision Records

## Status

Accepted

## Context

The repository spans multiple components with different teams, agents, and cadences. A single flat list of ADRs would conflate system-wide decisions with component-specific ones and make context scoping harder for both humans and coding agents.

## Decision

Use two levels of ADRs:

1. **Global ADRs** (`docs/adr/`) — System-wide decisions that affect architecture, security, privacy, observability, or cross-cutting concerns. All contributors must be aware of these.
2. **Component-local ADRs** (`<component>/docs/adr/`) — Decisions specific to a single component's implementation, interface choices, or technology selection. Relevant only within that component's bounded context.

Global ADRs take precedence over local ones when they conflict. Component ADRs should reference the relevant global ADR when building on it.

Requirements live in `docs/requirements/`. Design notes and specs live in component `docs/design/` directories.

## Consequences

- Coding agents and reviewers can scope their ADR reading to the component they are working on plus global ADRs.
- Cross-cutting decisions (security, privacy, logging format) are written once and referenced everywhere.
- Component teams have autonomy to record local decisions without polluting the global record.
