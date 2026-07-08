# Half-Life

Don't take the paper's word for it - measure your own model's context decay, then prove your fix
actually works.

## What this is

A self-paced workshop that teaches why LLMs degrade over long context - positional bias, length-
driven context rot, and compaction loss - to people who already work with LLMs daily. Every
exercise runs through your own coding-agent harness, scripted and non-interactive: you plant a
controlled variable (a needle's depth, a context's length, a fact placed before a real compaction
event), measure it against a stated threshold, and get a real number back. First, an **empirical
gate**: does the measured result clear the bar, yes or no. Second, a **conceptual check** from
Coachgremlin, this workshop's teaching agent (a role you run yourself, inside your own harness, not
a hosted service): did you actually design a single-variable experiment, and can you correctly
explain the result you got. A passing measurement is necessary but never sufficient on its own.

The name is the pitch: this workshop is about the decay curve, not just the symptom. "Context rot"
names what happened; "half-life" names the empirical question - how fast does reliability decay,
and as a function of what - the whole arc is built to answer.

**Who it's for:** agent-literate practitioners and LLM-app builders - comfortable driving a coding
agent daily, building RAG pipelines, or running long agent sessions - who want real intuition for
*why* long-context behavior degrades, not folklore. Not an intro-to-LLMs course (assumes you
already use these tools for real work) and not a research-paper reading group (the papers are
anchors, not the deliverable).

## Prerequisites

- Comfortable with git, the CLI, and reading a diff.
- Already using a coding-agent harness (Claude Code or equivalent) regularly, with one installed.
- Willing to run scripted, non-interactive harness invocations against your own API usage - each
  module states a capped run-count / rough token budget up front, but real usage still applies.

## How to start

```bash
git clone git@github.com:coderturtle/half-life.git
cd half-life
cat modules/README.md
```

Then work through `modules/` in order. Each module states a hard prerequisite on an earlier one:
skipping ahead means comparing against a baseline you haven't actually measured yet.

> **Current status: all six modules are skeleton only.** Each has a decided question, gate shape,
> and takeaway shape (see [`modules/README.md`](modules/README.md)), but no authored exercise script
> or real dry run yet. Watch `docs/build-log/` for progress, or [open an
> issue](https://github.com/coderturtle/half-life/issues) to ask.

## How the modules connect

Window mechanics has no prerequisite - everything later needs this vocabulary to state what's being
varied. Positional bias depends on it, and is the narrowest, most direct reproduction of prior
research. Context rot at scale depends on positional bias already being controlled for, since
isolating "does length alone matter" requires holding position fixed first. Compaction mechanics
depends only on window vocabulary, but is sequenced after both because what's lost during compaction
is far more legible once you've already measured what's lost from position and length. Mitigations
come last among the core modules because "this helped" is meaningless without an already-measured
baseline. A synthesis capstone closes the arc: given an uncovered phenomenon, design and defend an
original experiment that reuses an earlier module's own methodology. Full arc, gate tiers, and the
curriculum research behind it: [`modules/README.md`](modules/README.md).

## What you keep

Every module leaves you with something, not just a passed check: a context-inspection habit, a
reusable needle-in-haystack test script, a safe-context-budget measurement script, a pre/post-
compaction recall probe, a mitigation decision guide, and a personal context-diagnosis playbook
tying it all together. See [`modules/README.md`](modules/README.md#what-you-keep) for the full list.

## The teaching method

Our working hypothesis, not a settled finding: a real empirical tier (a scripted, scored
measurement) should make Coachgremlin's conceptual feedback easier to trust than an all-subjective
rubric could be. This subject has no compiler to reuse, unlike a language workshop - the empirical
tier had to be designed from scratch, and every module's rubric must acknowledge that an LLM-scored
measurement has real run-to-run variance a compiler doesn't. No module content or dry run exists yet
to test this bet against. See [`docs/workshop-design.md`](docs/workshop-design.md) for the full
reasoning, including where this is a bet, not proven pedagogy, and the real research this arc is
anchored to: Lost in the Middle, Kamradt's needle-in-a-haystack methodology, Chroma's Context Rot
report, and Anthropic's context-engineering guidance.

## Build in public

This workshop's own build is published as a dated journal at
`coderturtle.github.io/half-life` once the first deploy is triggered: the maintainer's record of
building the workshop and measuring these phenomena for real, written deliberately rather than
auto-generated from session logs.

## Something wrong?

This is early and imperfect by design. If a module reduces to "read this, then move on" instead of
a real measurement, or a link here is broken, [open an
issue](https://github.com/coderturtle/half-life/issues).

## Key docs

- [Workshop Design](docs/workshop-design.md): audience, format, empirical-gate teaching method, full
  module arc, canonical-curriculum anchor
- [Maintainers](docs/maintainers.md): internal/agent-facing docs, classification, documentation
  contract
