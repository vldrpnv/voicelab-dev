# Project structure open items and challenge questions

This document keeps the unresolved parts of the VoiceLab development discussion out of the accepted structure decision until they are turned into requirements, specs, or ADRs.

## Still unresolved after the structure update

- Which first workflows best prove the platform value.
- Which repository areas need implementation first versus placeholders only.
- When the current `src/` prototype should split into dedicated assistant-core and service packages.
- Which local component-level documentation conventions should be mandatory from the first implementation PR.

## Challenge questions grouped by area

### Product scope

- Which first workflows prove the platform value best?
- Which organic workflows are MVP-critical?
- What latency vs. patience tradeoff is acceptable?
- Should personality be global, per-user, or per-context?
- How much identity confidence is required before using private context?
- Which child-related use cases are allowed in MVP?

### Satellites, firmware, and wake word

- Which satellite hardware variants are supported first?
- Which wake word engine will be used initially?
- What is the target wake word, and which language/accent variants are needed?
- Which toolkit should power wake word training?
- What target false activation rate is acceptable at home?
- How far can firmware be modified without fighting upstream assumptions?
- Which firmware changes are mandatory versus nice-to-have?
- Which interactions belong on the satellite versus the central node?
- Is audio streamed to the central node, or does the satellite do partial ASR?

### Assistant core, output, and logging

- What exact timing budgets are realistic on a Mac mini plus satellites?
- Should acknowledgement be spoken, sound-based, LED-based, or configurable?
- Which commands must stay below two seconds?
- Which routing dimensions are required in MVP?
- Which requests are privacy-sensitive enough to forbid cloud?
- Which providers are acceptable for remote LLM, TTS, and ASR?
- Which tools come first: shopping list, calendar, Home Assistant, Spotify, notes, or something else?
- What is the minimum useful behavior when central services are degraded?
- Should detailed technical errors be visible only in logs or an admin UI?
- Which data should be cached, and for how long?
- How much detail should be spoken by default when something fails?
- Which recovery actions are safe to propose automatically?
- Should spoken-output sanitization be rule-based, LLM-based, or both?
- How should code, tables, URLs, and lists be handled in spoken mode?
- Which clients can display visual companion content?
- How will a user flag a bad response by voice?
- Where should golden fixtures live?
- How much data can be logged without privacy risk?
- Which tracing format should be used?
- Which dashboard or tooling is enough for MVP?
- Should raw audio be stored temporarily only?
- Should a trace ID ever be spoken?

### Process, testing, and repository management

- What change size requires an ADR?
- Which spec template should be used?
- How strict should test-first development be for prototypes?
- Should behavior scenarios use formal Gherkin or simple Markdown?
- What is the maximum task size for agent execution?
- Which changes can be auto-merged?
- Should CI reject broad unrelated diffs?
- How formal should authorship metadata be?
- What exact top-level structure should remain long-term?
- What naming convention should local ADRs use?
- How should duplication between global and local docs be prevented?
- Can CI detect missing docs updates?
- Should relevant records be mandatory in every issue?
- Which hardware behaviors need simulation first?
- What hardware acceptance suite is required before release?
- Which interfaces need contract tests first?
- Which developer test setups are MVP-critical?
- Which CI platform should be used?
- How should golden tests be updated without freezing behavior too much?
- Which protocol format should be used for contracts?
- Which failure cases are release blockers?
- Can TTS audio quality be evaluated automatically well enough?

### Deployment, security, privacy, and agent workflows

- Should deployment be push-based or pull-based?
- What is the acceptable risk level for private-network deployment?
- Is there enough hardware for a staging channel?
- What is the rollback target: previous image, git tag, firmware image, or another artifact?
- Should failed health checks trigger auto-rollback?
- Who reviews threat-model changes?
- Which secret-management solution should the local Mac mini use?
- Should commits be blocked locally with pre-commit secret scanning?
- How strict should security enforcement be in review?
- Which actions require stronger authentication than voice identity alone?
- How much TLS or mTLS is needed on the local network?
- What are the shared family-context versus private-context rules?
- How many enrollment samples are needed per user?
- What should be kept by default under the data-retention policy?
- Should cloud use be disclosed verbally, in admin logs, or both?
- Which agent platform will be tried first?
- Should agents be limited to one component per task?
- Can self-review be automated in PR comments?
- Should context packs be built manually first or automated early?
- How should agent uncertainty be handled in autonomous mode?
- What maximum PR size stays reviewable?
- How should raw notes be separated from accepted decisions?
- What ADR format and numbering scheme should be used?
- When should a design note become an ADR?
- Should requirements live in one global file or multiple files?
- How much implementation-journal content belongs in the repo?
- Should traceability use manual links or tooling?
