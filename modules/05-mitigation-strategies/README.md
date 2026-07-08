# Module 05: Mitigation Strategies

## The question this module answers

Does a real mitigation (retrieval, sub-agent context isolation, or structured note-taking) actually
beat the naive baseline I already measured?

## Where it sits in the arc

Fifth module. Prerequisite: **at least one of** [Module 02](../02-positional-bias/README.md),
[Module 03](../03-length-driven-context-rot/README.md), or
[Module 04](../04-compaction-mechanics/README.md) - a mitigation's "it helped" claim is meaningless
without an already-measured baseline failure to compare against, and this module reuses whichever
single baseline (positional, length-driven, or compaction-driven) the learner chooses to target; it
does not require having completed all three. Next:
[Module 06, Synthesis capstone](../06-synthesis-capstone/README.md), which must reuse this module's
or Module 04's methodology directly, not just repeat a depth/length sweep. See
[`modules/README.md`](../README.md) for the full arc and why this order.

## Learning objectives (placeholder: finalized when content is authored)

- Pick one prior measured failure (from Module 02, 03, or 04) and one real mitigation strategy to
  apply against it.
- Re-run that module's own scoring method against the mitigated version, producing an apples-to-
  apples before/after comparison, not a new, incomparable measurement.
- Report the outcome honestly, including "the mitigation didn't help" or "inconclusive" as valid,
  real results.

## Exercise material to draw from (not a spec: Coachgremlin authors the real exercise later)

Real material this module's exercise should be built from: Anthropic's [Effective context
engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
(September 2025) - retrieval, sub-agent context isolation, and structured note-taking as concrete,
practitioner-facing strategies. See
[`docs/workshop-design.md`](../../docs/workshop-design.md)'s curriculum-anchor section.

## Required gate (placeholder: shape decided now, real rubric written later)

- **Empirical tier.** The learner applies one mitigation (retrieval, sub-agent isolation, or
  structured notes) to one failure mode already measured in Module 02, 03, or 04, then reruns that
  earlier module's own scoring script against the mitigated approach. Pass: a real before/after
  numeric comparison is produced and reported, using the same scoring method as the original
  baseline (not a new, incomparable metric).
- **Conceptual tier (Coachgremlin).** Confirms the comparison is genuinely apples-to-apples (same
  variable, same scoring method, same or comparable context otherwise) and that the learner's stated
  conclusion (helped / didn't help / inconclusive) matches what the numbers actually show, rather
  than assuming the mitigation must have worked because it's the "recommended" strategy.

## Takeaway

A decision guide: which mitigation fits which failure mode, built from the learner's own before/
after measurements rather than copied from the Anthropic blog post. Packaged by Coachgremlin once
the rubric is met.

## Stop condition (placeholder)

The learner's before/after comparison clears the empirical tier and Coachgremlin confirms the
conceptual tier. Reading this page does not count: advancement requires a real mitigation applied
and measured against a real prior baseline.

---

> **Skeleton only.** This module has a decided question, arc position, gate shape, and takeaway
> shape. It has no authored exercise, script, or rubric yet: that's Coachgremlin's job, run later,
> per the Workshop Gremlin's Completion Condition (it stops before content exists). See
> [`modules/README.md`](../README.md) for workshop-wide status.
