# Project structure requirements

## Check against current `main`

The current `main` branch already implemented part of the issue intent before this change:

- The project was already framed as a broader local-first assistant platform, not just a Home Assistant intent handler.
- The existing context docs already covered assistant-core concerns such as routing, latency, quality, fallback behavior, privacy, and Home Assistant Voice Preview integration.
- The repository already had a small `src/` assistant-core prototype.

The current `main` branch did **not** yet implement these project-structure requirements:

- distinct top-level spaces for firmware, satellites, services, integrations, infrastructure, tooling, wake word work, and shared tests
- central documentation lanes for ADRs, requirements, and unresolved discussions
- an explicit mapping between the existing context material and the intended monorepo structure
- a dedicated unresolved-items document preserving the open questions from the planning discussion

## Adopted layout

```text
docs/
  adr/
  contexts/
  discussions/
  requirements/
src/
firmware/
satellites/
services/
integrations/
wakeword/
infra/
tooling/
tests/
```

## Mapping of existing content

- `docs/contexts/product.md` remains the seed product framing.
- `docs/contexts/domain.md` remains the domain boundary summary.
- `docs/contexts/architecture.md` remains the initial architecture snapshot.
- `docs/contexts/constraints.md` remains the initial constraint record.
- `src/` remains the assistant-core prototype area until there is enough implementation to split further.

## Structural rules going forward

- Cross-cutting decisions belong in `docs/adr/`.
- Repository-wide requirements belong in `docs/requirements/`.
- Unresolved planning notes and challenge questions belong in `docs/discussions/` until decided.
- New component work should live in its bounded top-level directory and keep its local documentation close to that code.
- Home Assistant-specific work should stay separate from assistant-core logic by favoring `integrations/` over placing integration code directly into `src/`.
