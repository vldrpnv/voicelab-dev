# Wake Word

## Purpose

Custom wake word training, evaluation, and model management for VoiceLab. This is a parallel project that runs alongside the main assistant development.

## Responsibilities

- Collect and manage training datasets for a custom wake word.
- Train, evaluate, and iterate on wake word models.
- Measure false accept rate (FAR) and false reject rate (FRR) under realistic household conditions.
- Export trained models for integration into satellite firmware.

## Directory Layout

```
datasets/     Training and evaluation data (see datasets/README.md)
experiments/  Training runs, configs, and experiment notes
models/       Exported and versioned wake word models
docs/adr/     Component-local architectural decisions
docs/design/  Design notes and evaluation plans
tests/        Automated evaluation scripts
```

## Key Constraints

- Custom wake word must not depend on "Hey Nabu" or other standard wake words in the final product.
- A temporary default wake word is acceptable as a development fallback only.
- FAR/FRR targets and test conditions (noisy room, family voices, TV/music) must be defined before evaluating models.

## Local ADRs

Component-specific decisions are in `docs/adr/`.

## Status

Not yet started. See [docs/discussions/unresolved-items-and-open-questions.md](../docs/discussions/unresolved-items-and-open-questions.md) for open questions on wake word engine selection and target word.
