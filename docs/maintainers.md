# Maintainers

This is the internal/agent-facing doc. Learners should read the top-level `README.md` instead; this
file is for anyone working on the workshop itself.

**Classification:** factory-output
**Lifecycle:** active
**Owner:** coderturtle
**Promotion target:** `none`

This repo has two goals:

1. **Ship a workshop** teaching why LLMs degrade over long context (positional bias, length-driven
   context rot, compaction loss) to agent-literate practitioners, taught by running every exercise
   through a real harness with a scripted, scored measurement as the primary gate, and Coachgremlin
   grading the conceptual layer on top.
2. **Feed evidence back into the reusable machinery**: this is the Workshop Gremlin's *third* real
   run (`terminal-velocity` was its first, `borrow-native` its second) and its first on a subject
   with no existing objective-checker tool to reuse (no compiler, no linter) — the empirical tier
   had to be invented from scratch. Findings from this run belong back in the canonical **Workshop
   Gremlin** and **Coachgremlin** definitions (`~/hekton/gremlins/`) once there's enough real
   evidence (a dry run) to justify a change, same discipline `borrow-native` used.

## Implementation Status

- 2026-07-07 — Scaffolded as factory-output (as `context-workshop`). Naming pass complete:
  **Half-Life**, chosen over Lost in the Middle, Context Rot, and Needle Native. Full rename
  executed (repo, remote, `.hekton/project.yaml`, repo-local mirror, live vault card).
- 2026-07-07 — [Workshop Design](workshop-design.md) drafted: 6-module arc anchored to real research
  (Lost in the Middle, Kamradt's needle-in-a-haystack methodology, Chroma's Context Rot report,
  Anthropic's context-engineering guidance, Claude Code's real compaction mechanism).
- 2026-07-07 — First [Workshop Review Panel](review-panel/2026-07-07-initial-design.md) run complete
  against the design docs — all seven personas returned distinct findings; cheap text fixes applied
  same pass, structural findings (per-module gate concreteness, cost bound, capstone distinctness)
  deferred to the module-skeleton pass.
- 2026-07-08 — Module skeleton (`modules/`), brand layer (`docs/brand.md`), and this maintainers
  split are done, addressing the deferred structural findings directly in each module's gate design.
  Build-log/Pages site is the remaining Completion Condition item — see [Next Actions](next-actions.md).

## Documentation Contract

Agents working here must inspect `.hekton/project.yaml` before structural changes, keep
`docs/session-log.md` current, record meaningful design decisions in `docs/decisions.md`, and update
`docs/next-actions.md` when the work queue changes.

Vault mutation is not allowed by default. The repo-local `mind-palace/` folder is only a mirror
draft; do not write to the live vault unless explicitly authorised in-session.

## Voice and style for published content

Anything a learner reads (README, module content, build-log entries, the site once built) follows
`docs/brand.md` — voice, hard rules (no em dashes, no unqualified reproduction/efficacy claims, no
"the model is broken" framing), banned phrases. Internal docs under `docs/` are working documents
and are exempt.

## Key Docs

- [Workshop Design](workshop-design.md) — audience, format, empirical-tier teaching method,
  curriculum-anchored module arc
- [Brand / Style Layer](brand.md) — voice, hard rules, visual identity
- [Workshop Review Panel Report](review-panel/2026-07-07-initial-design.md) — 7-persona critique of
  the design docs, first run
- [Modules index](../modules/README.md) — the full arc, gate tiers, cost guardrails, and per-module
  skeleton status
- [Session Log](session-log.md)
- [Decisions](decisions.md)
- [Risks](risks.md)
- [Project Walkthrough](project-walkthrough.md)
- [Next Actions](next-actions.md)
- [Operating Model](operating-model.md)
- [Human Understanding Check](human-understanding-check.md)
- [Depth Decision](depth-decision.md)
- [Retire / Promote Review](retire-promote-review.md)
