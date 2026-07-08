# Module 02: Positional Bias - Lost in the Middle

## The question this module answers

Does retrieval accuracy actually drop when the fact I need is buried in the middle of a long
context, on the harness I actually use?

## Where it sits in the arc

Second module. Prerequisite: [Module 01, Context Window Mechanics](../01-context-window-mechanics/README.md),
since you need token/window vocabulary to even state what's being varied before designing a
controlled test. Next: [Module 03, Context Rot at Scale](../03-context-rot-at-scale/README.md), which depends
on this module's depth variable already being controlled for before introducing length as a second
variable. See [`modules/README.md`](../README.md) for the full arc and why this order.

## Learning objectives (placeholder: finalized when content is authored)

- Design a single-variable experiment (depth) and predict, before running it, whether you expect a
  U-shaped accuracy curve.
- Run a capped, scripted needle-in-a-haystack sweep against your own harness and produce a real
  depth-vs-accuracy result, not an assumed one.
- Correctly explain the result you actually got, including the honest possibility that frontier
  Claude models show an attenuated curve versus the 2023-era models Liu et al. originally tested -
  **a flat or near-flat curve is a valid, real, defensible outcome here, not a failed exercise.**

## Exercise material to draw from (not a spec: Coachgremlin authors the real exercise later)

Real material this module's exercise should be built from: [Lost in the Middle: How Language Models
Use Long Contexts](https://arxiv.org/abs/2307.03172) (Liu et al., TACL 2024) for the original finding
and methodology, and [Greg Kamradt's Needle In A Haystack](https://github.com/gkamradt/needle-in-a-haystack)
for the standard depth-sweep technique this module's exercise is built directly on. See
[`docs/workshop-design.md`](../../docs/workshop-design.md)'s curriculum-anchor section.

## Required gate (placeholder: shape decided now, real rubric written later)

- **Empirical tier.** A scripted, non-interactive harness sweep (capped at ≤20 total invocations per
  the workshop-wide cost guardrail - see [`modules/README.md`](../README.md)) plants one factual
  needle at 5 stated depths (0%, 25%, 50%, 75%, 100%) across 2 context lengths, scoring retrieval
  accuracy per depth against the known correct answer. Pass: the learner produces a real depth-vs-
  accuracy result for both lengths - the result *shape* (U-curve, flat, or something else) is not
  itself gated; producing and correctly reporting a real measurement is.
- **Conceptual tier (Coachgremlin).** Confirms the experiment held every variable but depth
  constant (same haystack content, same needle, same length within each sweep), and that the
  learner's explanation matches whichever result they actually got - including defending a flat
  result with a real hypothesis (e.g. citing model-generation improvements since 2023) rather than
  treating it as an exercise failure.

## Takeaway

A reusable needle-in-haystack test harness script, parameterized so the learner can point it at
their own tasks later. Packaged by Coachgremlin once the rubric is met.

## Stop condition (placeholder)

The learner's sweep clears the empirical tier (a real, reported depth-vs-accuracy result across
both lengths, within the run-count cap) and Coachgremlin confirms the conceptual tier. Reading this
page does not count: advancement requires a script that was actually run against the learner's own
harness.

---

> **Skeleton only.** This module has a decided question, arc position, gate shape, and takeaway
> shape. It has no authored exercise, script, or rubric yet: that's Coachgremlin's job, run later,
> per the Workshop Gremlin's Completion Condition (it stops before content exists). See
> [`modules/README.md`](../README.md) for workshop-wide status.
