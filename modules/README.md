# Modules

Half-Life's spine is a measurement dependency, not a compiler dependency: **window vocabulary →
positional bias → length-driven rot → compaction mechanics → mitigations**, then a synthesis
capstone. Work through them in order - each module's own measured baseline is what the next
module's comparison depends on.

Every module's core exercise runs through your own coding-agent harness (Claude Code CLI/SDK),
scripted and non-interactive, never a raw HTTP API call and never a manually pasted session. Two
gates, not one: an **empirical tier** (a scripted run against controlled variables, scored pass/fail
or numerically against a stated threshold - no judgment call) and a **conceptual tier**
(Coachgremlin, checking whether the learner correctly explains *why* the measured result looks the
way it does, and whether the experiment actually isolated one variable). See
[`docs/workshop-design.md`](../docs/workshop-design.md) for the full thesis and the
canonical-curriculum-anchor research behind this arc, and
[`docs/review-panel/2026-07-07-initial-design.md`](../docs/review-panel/2026-07-07-initial-design.md)
for the first design-stage critique this arc responds to.

**Hands-on by design, not passive text.** No module here completes by reading it. Every module
states a required gate: a real measurement you produce, checked first mechanically (does the number
clear the stated bar), then conceptually (do you correctly explain it). Every gate also has a
stated **takeaway**: you keep something reusable, not just proof you ran the experiment.

> **Content status: all six modules are skeleton only.** Each has a decided question, arc position,
> gate shape, and takeaway shape (below). None has an authored exercise script, scoring harness, or
> real dry run yet - that's Coachgremlin's job, run later, one module at a time, per the Workshop
> Gremlin's own Completion Condition (it stops before content exists).

## Cost & scope guardrails (applies to every module)

Added directly in response to this workshop's own first Review Panel pass, which independently
flagged this gap from two angles (learner-cost and safety): every scripted parameter-sweep exercise
(Modules 02, 03 especially) must ship with a **stated run-count and rough token-budget cap** as part
of its authored content, not left open-ended. Default ceiling for this arc, to be refined per module
by Coachgremlin at authoring time: **no more than ~20 scripted harness invocations per module
exercise**, and a printed token-usage estimate before a learner's script fans out into a full sweep.
This is a design-time ceiling, not yet validated against a real authored exercise - flag it if a
later module genuinely needs more.

All haystack/filler content used in any exercise must be synthetic or public-domain text (e.g. essay
corpora, generated lorem-style filler) - never real logs, internal docs, or credential-shaped
strings, even for realism.

## The arc

Each module names its **hard prerequisite** explicitly, per the Gremlin's concept-dependency-arc
requirement.

| # | Module | Hard prerequisite | The question it answers | Required gate (once authored) |
|---|---|---|---|---|
| 01 | [Context Window Mechanics](01-context-window-mechanics/README.md) | none (assumes daily LLM/agent use) | What's actually taking up space in my context window right now, and why doesn't "bigger window" mean "free window"? | A scripted session progressively loads known-sized content; self-reported `/context` usage is checked against an independently measured token count, within a stated tolerance (empirical) + Coachgremlin confirms the learner can correctly attribute where the budget went, not just cite a total (conceptual) |
| 02 | [Positional Bias - Lost in the Middle](02-positional-bias/README.md) | 01 | Does retrieval accuracy actually drop when the fact I need is buried mid-context, on the harness I actually use? | A capped sweep (≤20 runs) plants one needle at 5 stated depths across 2 context lengths and scores retrieval accuracy per depth (empirical) + Coachgremlin confirms the experiment held every variable but depth constant, and that the learner correctly explains *whichever* result they got - a flat curve is a valid, real outcome on frontier models, not a failed exercise (conceptual) |
| 03 | [Context Rot at Scale](03-context-rot-at-scale/README.md) | 02 (isolating length requires already controlling for position) | Does accuracy degrade with length alone, and does a coherent haystack actually help or hurt? | A capped sweep varies length across ≥3 points spanning a 4x range at fixed depth, plus one coherent-vs-shuffled comparison at fixed length, both scored (empirical) + Coachgremlin confirms the learner reports the shuffled-vs-coherent result honestly, whichever direction it comes out, rather than assuming it must match the Chroma report (conceptual) |
| 04 | [Compaction Mechanics](04-compaction-mechanics/README.md) | 01 (needs window vocabulary); benefits from 02+03's intuition, not hard-blocked by them | When my harness compacts for real, what actually survives and what's silently lost? | A real session (not a simulator) plants a fact before the compaction trigger, drives past it, and probes recall post-compaction vs. a pre-compaction control, repeated ≥3 trials to account for run-to-run variance, reporting a numeric recall delta (empirical) + Coachgremlin confirms the learner can name *which* categories of content survived vs. were dropped, matching or contradicting Claude Code's own documented behavior (conceptual) |
| 05 | [Mitigation Strategies](05-mitigation-strategies/README.md) | 02, 03, 04 (a mitigation's "it helped" claim needs an already-measured baseline) | Does a real mitigation (retrieval, sub-agent isolation, structured notes) actually beat the naive baseline I already measured? | The learner applies one mitigation to a failure mode measured in 02, 03, or 04, reruns that module's own scoring script, and reports a before/after delta (empirical) + Coachgremlin confirms the comparison is apples-to-apples (same variable, same scoring method as the original baseline) and the conclusion (helped / didn't / inconclusive) is honestly stated (conceptual) |
| 06 | [Synthesis capstone](06-synthesis-capstone/README.md) | all of the above | Given a context-behavior phenomenon nobody told you about, can you design and defend an original empirical test of it? | The learner designs an original experiment on an uncovered phenomenon (e.g. attention sink, distractor semantic similarity, multi-document order sensitivity) that explicitly reuses either Module 04's pre/post-comparison methodology or Module 05's before/after-mitigation methodology, not just Module 02/03's depth/length sweep pattern again (empirical) + a written defense connecting the new finding back to at least one earlier module's own measured result, which Coachgremlin confirms is a genuine connection, not a restated finding wearing new variable names (conceptual) |

## Why this order

This is this workshop's own editorial synthesis, not an independently validated pedagogical finding
(same honesty caveat `terminal-velocity`/`borrow-native` applied to their own arcs). Window mechanics
comes first because every later experiment needs the vocabulary to even state what's being varied.
Positional bias comes next because it's the narrowest, best-established finding and the most direct
reproduction of prior art. Context rot at scale depends on positional bias already being controlled
for, because isolating "does length alone matter" requires holding position roughly fixed.
Compaction sits somewhat apart (it depends only on Module 01's vocabulary) but is sequenced after
02-03 deliberately: what's lost during compaction is far more legible once a learner has already
directly measured what's lost from position and length alone. Mitigations come last among the core
modules because a mitigation's "it helped" claim is meaningless without an already-measured baseline
to compare against. Full reasoning: [`docs/workshop-design.md`](../docs/workshop-design.md#why-this-order).

## What you keep

Per the Gremlin's takeaway requirement, every module's gate produces something reusable, not just a
passed check. Concrete takeaways are Coachgremlin's job at content-building time, but the intended
shape:

| # | Module | Intended takeaway shape |
|---|---|---|
| 01 | Context Window Mechanics | A personal context-inspection habit/Skill for triaging where the budget went before assuming "the model just forgot" |
| 02 | Positional Bias | A reusable needle-in-haystack test harness script, parameterized for the learner's own tasks |
| 03 | Context Rot at Scale | A "safe context budget" measurement script - the learner's own empirical answer to how much of a model's window can actually be trusted |
| 04 | Compaction Mechanics | A pre/post-compaction recall probe the learner can re-run on any real session |
| 05 | Mitigation Strategies | A decision guide: which mitigation fits which failure mode, built from the learner's own before/after measurements |
| 06 | Synthesis capstone | A personal context-diagnosis playbook compressing the whole arc, built from a defended original experiment |

## Gate tiers (every module uses this vocabulary)

| Tier | What it is |
|---|---|
| Empirical (primary) | A scripted harness run against controlled variables, scored pass/fail or numerically against a stated threshold - clears the bar or it doesn't, no judgment call. This workshop's invented equivalent of `borrow-native`'s compiler/clippy gate; unlike a compiler, the instrument itself has real run-to-run variance (sampling, model-version drift), which every module's authored rubric must acknowledge rather than treat as deterministic in the compiler sense. |
| Conceptual (secondary, Coachgremlin) | Did the learner correctly explain the measured result and design a genuinely single-variable experiment, rather than just observe that something happened? |

**Working hypothesis, not yet evidenced:** a real empirical tier should make Coachgremlin's job
easier and more trustworthy than an all-subjective rubric, the same bet `borrow-native` made with
its compiler. No module content or dry run exists yet to test this against.
