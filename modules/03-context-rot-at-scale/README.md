# Module 03: Context Rot at Scale

## The question this module answers

Does accuracy degrade with input length alone, independent of position, and does structuring the
haystack coherently actually help or hurt?

## Where it sits in the arc

Third module. Prerequisite: [Module 02, Positional Bias](../02-positional-bias/README.md) -
isolating "does length alone matter" requires holding position roughly fixed first, using a depth
already characterized by Module 02's own measurement; attempting length and position as
simultaneous unknowns would confound both variables. Next: [Module 04, Compaction
Mechanics](../04-compaction-mechanics/README.md), which depends only on Module 01's vocabulary but
is far more legible once a learner has already directly measured what's lost from position and
length alone. See [`modules/README.md`](../README.md) for the full arc and why this order.

## Learning objectives (placeholder: finalized when content is authored)

- Design an experiment that varies length while holding position fixed, using a depth already
  characterized in Module 02.
- Run a capped, scripted sweep across multiple context lengths and produce a real length-vs-
  accuracy result.
- Run and honestly report a coherent-vs-shuffled haystack comparison, including the
  counterintuitive possibility (confirmed directly against Chroma's primary source during this
  workshop's own Review Panel pass - see `docs/review-panel/2026-07-07-initial-design.md`) that
  *coherent, well-structured input degrades accuracy more than shuffled input does*.

## Exercise material to draw from (not a spec: Coachgremlin authors the real exercise later)

Real material this module's exercise should be built from: [Context Rot: How Increasing Input
Tokens Impacts LLM Performance](https://www.trychroma.com/research/context-rot) (Hong, Troynikov,
Huber - Chroma Research, July 2025), the most current, comprehensive empirical study of this exact
question across 18 models. See [`docs/workshop-design.md`](../../docs/workshop-design.md)'s
curriculum-anchor section.

## Required gate (placeholder: shape decided now, real rubric written later)

- **Empirical tier.** A scripted, non-interactive sweep (capped at ≤20 total invocations per the
  workshop-wide cost guardrail - see [`modules/README.md`](../README.md)) varies total context
  length across at least 3 points spanning a 4x range, at a depth already characterized in Module
  02, scoring retrieval accuracy per length. Separately, one coherent-vs-shuffled haystack
  comparison at a single fixed length, also scored. Pass: both results are produced and reported -
  the direction of the coherent-vs-shuffled result is not itself gated; producing and honestly
  reporting the real measurement is (do not assume it must match Chroma's finding without checking).
- **Conceptual tier (Coachgremlin).** Confirms position was genuinely held fixed across the length
  sweep (not accidentally reintroduced as a second variable), and that the learner reports the
  coherent-vs-shuffled result honestly, whichever direction it comes out, with a real attempted
  explanation rather than a shrug.

## Takeaway

A "safe context budget" measurement script - the learner's own empirical answer to how much of a
given model's window can actually be trusted for a given task, not the marketed number. Packaged by
Coachgremlin once the rubric is met.

## Stop condition (placeholder)

The learner's length sweep and coherent-vs-shuffled comparison both clear the empirical tier, and
Coachgremlin confirms the conceptual tier. Reading this page does not count: advancement requires
scripts that were actually run against the learner's own harness.

---

> **Skeleton only.** This module has a decided question, arc position, gate shape, and takeaway
> shape. It has no authored exercise, script, or rubric yet: that's Coachgremlin's job, run later,
> per the Workshop Gremlin's Completion Condition (it stops before content exists). See
> [`modules/README.md`](../README.md) for workshop-wide status.
