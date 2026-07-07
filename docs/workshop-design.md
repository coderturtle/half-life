# Workshop Design

> **Half-Life.** Naming pass complete (candidates: Half-Life, Lost in the Middle, Context Rot,
> Needle Native — all GitHub-slug-checked under `coderturtle` before presenting). This doc is
> drafted after the name was chosen, so it uses the final name throughout.

## The one-line problem

Practitioners who work with LLMs daily keep hitting the same moment — "I gave it all the
information, why did it forget the thing I said at the top?" — and treat it as a mysterious model
failure rather than a well-studied, named, *measurable* phenomenon. There's real research on
exactly this (positional bias, context rot, compaction lossiness), and real vendor guidance on what
to do about it, but almost nobody who hits the symptom has read the papers, and almost nobody who's
read the papers has reproduced the finding themselves against their own tools. This workshop closes
that gap empirically: learners don't read about context rot, they measure it, on their own harness,
then measure whether a mitigation actually helps.

## Audience

Agent-literate practitioners and LLM-app builders — comfortable driving a coding agent daily,
building RAG pipelines, or running long agent sessions — who want real intuition (not folklore) for
*why* long-context behavior degrades and *how* to design around it. Not an intro-to-LLMs course
(assumes the reader already uses these tools for real work) and not a research-paper reading group
(the papers are anchors, not the deliverable).

## Format

Self-paced, public repo. Matches `terminal-velocity`/`borrow-native`'s precedent — no facilitator
required, scales without a cohort.

## Subject vs. method (see `~/hekton/gremlins/workshop/workshop-gremlin.md`'s "Variant: Tech/Language Workshops")

Named separately, per this factory's standing rule since `borrow-native`:

- **Subject:** context windows and their effect on LLM behavior — size limits, positional bias,
  context rot, compaction/summarization loss, and what mitigates each.
- **Method:** harness-first empirical measurement. Every exercise runs through the learner's own
  Claude Code CLI/SDK in scripted, non-interactive form (`claude -p` or the Agent SDK driving
  repeatable runs with controlled variables), never a raw HTTP API script and never a manually
  pasted interactive session. The harness stays the classroom, same as `terminal-velocity`'s thesis
  — but here it's also the lab instrument the learner uses to take a real measurement.

The hook is the combination: "don't take the paper's word for it, or the vendor blog's word for it
— reproduce the finding yourself, against your own tool, then prove your fix actually works."

## The teaching method: empirical, with a designed-experiment gate

This subject has no compiler and no cargo test — but it does have something structurally
equivalent: a **designed experiment that produces a real, scoreable measurement**. Two gate tiers,
mirroring `borrow-native`'s deterministic/conceptual split but built from scratch for this subject
(this workshop has no existing objective-checker tool to reuse, unlike a compiler):

1. **Empirical tier (primary).** A scripted harness run against controlled variables (context
   length, needle depth, distractor count, compression ratio, pre/post-compaction timing) produces
   a real pass/fail or numeric score against a stated expected answer or threshold — e.g., "recall
   the planted fact correctly in 4/5 depths" or "post-compaction recall accuracy within N points of
   pre-compaction baseline." This either clears the bar or it doesn't.
2. **Conceptual tier (secondary, Coachgremlin).** Did the learner correctly *explain* why the
   measured result looks the way it does (attention/positional bias, distractor interference,
   summarization lossiness) rather than just observe that it happened? Did they design a valid,
   single-variable experiment rather than a confounded one that can't actually isolate the effect
   claimed?

**Working hypothesis, not yet evidenced** (same honesty discipline as `borrow-native`'s own
deterministic-gate claim): a real empirical tier should make Coachgremlin's job easier and more
trustworthy than `terminal-velocity`'s all-subjective rubric, the same bet `borrow-native` made
with its compiler. No module content or dry run exists yet to test this against — flagged here so
the claim isn't overstated at design time.

## Canonical-curriculum anchor (research pass, 2026-07-07)

This subject already has real, current research and vendor guidance. Rather than invent a teaching
sequence from scratch, this workshop's arc is anchored to it directly:

- **[Lost in the Middle: How Language Models Use Long Contexts](https://arxiv.org/abs/2307.03172)**
  (Liu et al., TACL 2024) — the seminal finding that retrieval accuracy is highest when relevant
  information sits at the start or end of a context and drops significantly when it's in the
  middle (the "U-shaped curve"). The foundational positional-bias result this workshop's Module 02
  reproduces directly.
- **[Needle In A Haystack](https://github.com/Arize-ai/LLMTest_NeedleInAHaystack2)** methodology
  (Greg Kamradt, 2023) — the standard empirical technique for measuring exactly this: plant a
  specific fact ("the needle") at varying depths within a larger body of text (the "haystack") and
  measure retrieval accuracy across depth × length. This workshop's core experiment scaffold is
  built directly on this methodology.
- **[Context Rot: How Increasing Input Tokens Impacts LLM Performance](https://research.trychroma.com/context-rot)**
  (Hong, Troynikov, Huber — Chroma Research, July 2025) — the most current, comprehensive empirical
  study: 18 models, controlled experiments showing accuracy degrades with length itself (not just
  position), that distractors and haystack structure matter non-uniformly, and — the counter­
  intuitive finding this workshop's Module 03 specifically targets — that *coherent, well-structured
  input degrades attention more than shuffled input does*. This is the phenomenon this workshop is
  named after, and the paper that gives "context rot" its name.
- **[Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)**
  (Anthropic Engineering Blog, September 2025) — the practitioner-facing "what do you do about it"
  layer: compaction, sub-agent context isolation, structured note-taking, and retrieval as
  deliberate strategies for managing the token budget, not just prompting harder. Anchors this
  workshop's Module 05 (mitigations).
- **[Claude Code's real `/compact` mechanism](https://platform.claude.com/docs/en/build-with-claude/compaction)**
  — not a paper, but a real, inspectable product behavior: at ~95% context utilization, Claude Code
  runs a summarization pass over the conversation, replacing full history with a condensed summary
  that keeps file states/decisions/constraints but discards intermediate reasoning and verbose tool
  output. Because the learner's own harness *is* this tool, Module 04 doesn't need a synthetic
  compaction simulator — it measures the real thing.

**Differentiator against all of these:** none of them are hands-on for a practitioner — the papers
are read, not reproduced; the blog post is prescriptive, not verified; Kamradt's methodology is run
by researchers and vendors benchmarking models, not by the practitioner hitting the symptom in their
own work. This workshop's bet is that turning "trust the paper" into "reproduce it yourself, against
your own tool, then prove your own mitigation works" is a genuine addition — a hypothesis this
workshop is testing, not a finding it's reporting.

## The module arc

Each module names its **hard prerequisite** explicitly, per the Gremlin's concept-dependency-arc
requirement — not just a position in a plausible-looking list.

| # | Module | Hard prerequisite | Canonical anchor |
|---|---|---|---|
| 01 | Context Window Mechanics | none (assumes daily LLM/agent use) | Background: tokens, attention cost, KV cache — why "bigger window" isn't free. First hands-on task: inspect your own harness's real-time context/token usage. |
| 02 | Positional Bias — Lost in the Middle | 01 (needs token/window vocabulary to design a controlled test) | Liu et al. 2023; Kamradt's needle-in-a-haystack methodology |
| 03 | Context Rot at Scale | 02 (isolating length-as-a-variable requires already controlling for position) | Chroma's Context Rot report — length-driven degradation, distractor/structure effects, the coherent-input-degrades-more-than-shuffled finding |
| 04 | Compaction & Compression Mechanics | 01 (needs window vocabulary); benefits from 02+03's intuition about what's lost, but not hard-blocked by them | Claude Code's real `/compact` behavior — what survives a real compaction vs. what's discarded |
| 05 | Mitigation Strategies | 02, 03, 04 (you need to have measured a failure mode before you can measure whether a fix helps it) | Anthropic's "Effective context engineering for AI agents" — retrieval, sub-agent isolation, structured note-taking |
| 06 | Synthesis capstone | all of the above | Learner designs and runs an *original* experiment on a phenomenon not explicitly covered (e.g. attention sink, distractor semantic similarity, multi-document order sensitivity), and defends the result |

### Why this order

**This is this workshop's own editorial synthesis, not an independently validated pedagogical
finding** — same honesty caveat `terminal-velocity`/`borrow-native` applied to their own arcs.
Window mechanics comes first because every later experiment needs the vocabulary (tokens, KV cache,
why attention cost isn't linear) to even state what's being varied. Positional bias comes next
because it's the narrowest, best-established finding (one variable: depth) and the most direct
reproduction of prior art (Kamradt's methodology, almost unchanged). Context rot at scale depends on
positional bias being already controlled for, because isolating "does length alone matter" requires
holding position roughly fixed — attempting it first would confound the two variables. Compaction
sits somewhat apart (it depends only on Module 01's vocabulary) but is sequenced after 02-03
deliberately: understanding *what* gets lost during compaction is far more legible once a learner has
already directly measured what gets lost from position and length alone. Mitigations come last among
the core modules because a mitigation's "it helped" claim is meaningless without an already-measured
baseline from 02-04 to compare against.

## What you keep

Per the Gremlin's takeaway requirement (`workshop-gremlin.md` Design Principle 4): every module's
gate produces something reusable, not just a passed check. Concrete takeaways are Coachgremlin's job
at content-building time (not this design pass), but the intended *shape* per module:

| # | Module | Intended takeaway shape |
|---|---|---|
| 01 | Context Window Mechanics | A personal "what's actually in my context right now" inspection habit/Skill |
| 02 | Positional Bias | A reusable needle-in-haystack test harness script, parameterized for the learner's own tasks |
| 03 | Context Rot at Scale | A "safe context budget" measurement script — the learner's own empirical answer to "how much of this model's window can I actually trust," not the marketed number |
| 04 | Compaction & Compression Mechanics | A pre/post-compaction recall probe the learner can re-run on any real session |
| 05 | Mitigation Strategies | A decision guide: which mitigation (retrieval, sub-agent isolation, structured notes) fits which failure mode, built from the learner's own before/after measurements |
| 06 | Synthesis capstone | A personal context-diagnosis playbook compressing the whole arc, built from a defended original experiment, not a substitute for it |

## Build-in-public build log

Published as a dated build-log/journal via GitHub Pages, using the same Astro-on-Pages pipeline
`terminal-velocity` built and `borrow-native` reused (Content Layer API, `base`-aware links,
`deploy-pages` Action) — no new pattern needed here.

## What's explicitly out of scope for this design pass

- All module content, exercise scripts, and scoring harnesses — Coachgremlin's job, run later, one
  module at a time.
- The actual Astro site content and first Pages deploy.
- Any claim that the empirical-tier/conceptual-tier gate split works well in practice — untested
  until a real module dry run exists (same caveat `borrow-native` applied to its own gate).
