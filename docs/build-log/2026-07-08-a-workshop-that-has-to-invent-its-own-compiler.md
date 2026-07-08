---
title: "A Workshop That Has to Invent Its Own Compiler"
description: "Borrow Native had cargo test for free. Half-Life had to design its own objective gate from scratch, and the review panel found real bugs in that design before a single exercise existed."
pubDate: 2026-07-08T09:00:00
tags: ["build-log", "workshop-gremlin", "review-panel", "coachgremlin"]
draft: false
---

Terminal Velocity's gate was entirely subjective: Coachgremlin's rubric, and nothing else, decided
whether an exercise passed. Borrow Native fixed that by picking a subject with a compiler already
built in. Half-Life doesn't have that luxury. There's no `cargo test` for "did the model forget the
fact I planted." If this workshop was going to have an objective gate at all, it had to be designed
from nothing: a scripted, scored measurement standing in for a compiler that doesn't exist for this
subject.

That's a genuinely different kind of workshop than the first two, and it showed up immediately in
where the mistakes were. Borrow Native's review panel mostly caught prose problems and one
citation error. Half-Life's caught real methodology bugs, twice.

The first pass, against the design doc, found the predictable thing: an "empirical tier" claimed
uniformly across six modules but only concretely specified for two of them. Easy to fix once
named. The second pass, against the actual module skeleton, found something worse: Module 04's
gate compared recall before and after a real compaction event, and called the difference
"compaction loss." Two reviewers, working independently from different angles, both landed on the
same problem: that comparison can't actually tell "compaction ate it" apart from "it was just
farther away," because more tokens between a fact and a probe cause a positional-decay effect all
by themselves, the exact thing two earlier modules in this same arc already exist to measure. A
design that measures its own confound and calls it a finding isn't a defect this workshop can
afford, since the whole pitch is "don't trust the number, verify it yourself." The fix was a third
control arm: same distance, compaction not triggered. Obvious in hindsight. Not in the first draft.

The same pass caught the workshop's own banned phrase sitting in a module title. "Context Rot at
Scale" used "at scale," which `docs/brand.md` bans unless the content proves the scale, and nothing
about a four-times length sweep proves anything at scale. Renamed to "Length-Driven Context Rot."
Small, but the kind of thing that's invisible until a fresh reviewer who isn't the one who wrote
the rule reads the module list next to the rule itself.

What's actually here today: a scaffolded public repo, a chosen name, a design doc anchored to real,
verified research (not just cited, checked directly against primary sources during review, twice),
six module skeletons with a decided question, a concrete empirical gate, and a takeaway each, two
rounds of review with real findings applied, and no content. That last part is the honest stopping
point this Gremlin's own contract sets for itself. Coachgremlin's two-tier grading, empirical first,
conceptual second, is designed and has never graded a real attempt at anything. Whether a real
learner can actually run these scripted experiments and get an honest number back is still
completely untested. That's the next real test, and it isn't this session's to run.
