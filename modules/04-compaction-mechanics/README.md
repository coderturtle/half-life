# Module 04: Compaction Mechanics

## The question this module answers

When my harness compacts for real, what actually survives and what's silently lost?

## Where it sits in the arc

Fourth module. Prerequisite: [Module 01, Context Window Mechanics](../01-context-window-mechanics/README.md),
which needs window vocabulary, nothing more. This module's dependency is soft, not hard: it benefits
from Modules 02-03's intuition about what gets lost from position and length, but isn't blocked by
either - what's lost during compaction is simply far more legible once a learner has already
directly measured what's lost from position and length alone, which is why it's sequenced here
rather than immediately after Module 01. Next: [Module 05, Mitigation
Strategies](../05-mitigation-strategies/README.md), which needs an already-measured baseline
failure (from this module or either of the two before it) before a mitigation's "it helped" claim
means anything. See [`modules/README.md`](../README.md) for the full arc and why this order.

## Learning objectives (placeholder: finalized when content is authored)

- Trigger a real compaction event in your own harness (not a simulated one) and observe it directly.
- Design a pre/post-compaction recall probe that isolates what a specific planted fact's survival
  depends on.
- Report a numeric recall delta across repeated trials, accounting for the real run-to-run variance
  inherent in an LLM-scored measurement - this module's gate is explicitly *not* deterministic the
  way a compiler is, and the rubric must say so.

## Exercise material to draw from (not a spec: Coachgremlin authors the real exercise later)

Real material this module's exercise should be built from: Claude Code's own documented
auto-compaction behavior (`code.claude.com/docs/en/how-claude-code-works`'s "When context fills up"
section - "clears older tool outputs first, then summarizes the conversation if needed"), which
this module measures directly rather than assuming. See
[`docs/workshop-design.md`](../../docs/workshop-design.md)'s curriculum-anchor section for the full
research, including the correction already made there: don't cite an unverified specific trigger
percentage as fact.

## Required gate (placeholder: shape decided now, real rubric written later)

- **Empirical tier.** A real scripted session plants a specific fact, then drives past the harness's
  actual compaction trigger (however that's reached in practice - filling context with real or
  synthetic tool output, not a synthetic compaction simulator), then probes recall of the planted
  fact. Compares against a control probe run pre-compaction in an otherwise-identical session.
  Repeated across at least 3 trials to account for the measurement's own run-to-run variance. Pass:
  a numeric recall accuracy delta is reported (pre vs. post), with the variance across trials also
  reported, not just a single-run number presented as settled.
- **Conceptual tier (Coachgremlin).** Confirms the learner can name which categories of content
  survived vs. were dropped (matching or contradicting Claude Code's own documented "clears tool
  outputs first, then summarizes" behavior) and that they didn't treat a single trial as conclusive
  given the measurement's inherent variance.

## Takeaway

A pre/post-compaction recall probe script the learner can re-run on any real session of their own
later. Packaged by Coachgremlin once the rubric is met.

## Stop condition (placeholder)

The learner's probe clears the empirical tier (a reported delta across ≥3 trials) and Coachgremlin
confirms the conceptual tier. Reading this page does not count: advancement requires a real
compaction event triggered and measured in the learner's own harness.

---

> **Skeleton only.** This module has a decided question, arc position, gate shape, and takeaway
> shape. It has no authored exercise, script, or rubric yet: that's Coachgremlin's job, run later,
> per the Workshop Gremlin's Completion Condition (it stops before content exists). See
> [`modules/README.md`](../README.md) for workshop-wide status.
