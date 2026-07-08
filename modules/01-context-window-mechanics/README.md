# Module 01: Context Window Mechanics

## The question this module answers

What's actually taking up space in my context window right now, and why doesn't "bigger window"
mean "free window"?

## Where it sits in the arc

First module. No prior module: every later experiment needs this module's vocabulary (tokens,
attention cost, KV cache) to even state what's being varied. Next: [Module 02, Positional Bias -
Lost in the Middle](../02-positional-bias/README.md), the first module that actually plants a
controlled variable and measures against it - the hinge is that you can't design a controlled
context experiment until you can say precisely what's in the context to begin with. See
[`modules/README.md`](../README.md) for the full arc and why this order.

## Learning objectives (placeholder: finalized when content is authored)

- Explain, in your own words, why attention cost isn't linear in context length, and what that
  implies about "bigger window" not being "free window."
- Read your own harness's real-time context/token reporting and correctly attribute where the
  budget is going (system prompt, CLAUDE.md, tool outputs, file contents, conversation history).
- Distinguish a model's context *window* (the hard token limit) from its context *reliability*
  (how much of that window actually gets used well) - the distinction the rest of this workshop is
  built on.

## Exercise material to draw from (not a spec: Coachgremlin authors the real exercise later)

Real material this module's exercise should be built from: Anthropic's own documentation on the
context window and `/context` (`code.claude.com/docs/en/how-claude-code-works`'s "The context
window" section), and Anthropic's "Effective context engineering for AI agents" blog post for the
practitioner-facing framing of what's actually competing for space. See
[`docs/workshop-design.md`](../../docs/workshop-design.md)'s curriculum-anchor section for the full
research this arc is grounded in.

## Required gate (placeholder: shape decided now, real rubric written later)

- **Empirical tier.** A scripted session progressively loads content of known, independently
  measured size (e.g. files of a stated token count via a separate counting script), checkpointing
  `/context`'s self-reported usage after each load. Pass: self-reported usage tracks the
  independently measured total within a stated tolerance (e.g. ±10%) across at least 3 checkpoints.
  This is a read-only inspection exercise - no parameter sweep, no cost-bound concern the way
  Modules 02-03 have.
- **Conceptual tier (Coachgremlin).** Confirms the learner can correctly attribute where the budget
  went (not just report a total number) and can state, without looking it up, why doubling the
  window size doesn't double how much of it is usable reliably - a claim this module doesn't yet
  prove (that's Modules 02-03), but should be stated as the hypothesis the rest of the workshop
  tests.

## Takeaway

A personal context-inspection habit, packaged as a Claude Code Skill: a checklist for triaging where
the token budget actually went before assuming "the model just forgot." Packaged by Coachgremlin
once the rubric is met.

## Stop condition (placeholder)

The learner's own measurement clears the empirical tier's stated tolerance, and Coachgremlin
confirms the conceptual tier. Reading this page does not count: advancement requires a real
`/context` measurement Coachgremlin has actually reviewed against the gate above.

---

> **Skeleton only.** This module has a decided question, arc position, gate shape, and takeaway
> shape. It has no authored exercise, script, or rubric yet: that's Coachgremlin's job, run later,
> per the Workshop Gremlin's Completion Condition (it stops before content exists). See
> [`modules/README.md`](../README.md) for workshop-wide status.
