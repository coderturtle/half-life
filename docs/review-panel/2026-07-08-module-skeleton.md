# Workshop Review Panel — Module Skeleton Re-Run

**Date:** 2026-07-08
**Scope:** `README.md`, `docs/brand.md`, `modules/README.md`, and all 6 module READMEs — new content
built since the 2026-07-07 design-doc-only pass.
**Trigger:** the panel's own "significant content revision... that hasn't had outside eyes on it"
clause. Content is still skeleton-only (no authored exercises/scripts/dry runs).

Seven personas reviewed independently and in parallel. Raw critiques in full below; synthesis and
prioritized action list follow.

## Verification of the prior pass's deferred findings

Three personas were asked to specifically verify whether the 2026-07-07 pass's deferred structural
findings were actually resolved, not just assume it:

- **Cost/scope bound: resolved.** `modules/README.md`'s guardrail section is real and applied.
- **Capstone distinctness: resolved and checkable.** Module 06 requires reusing Module 04's or 05's
  methodology as a structural, checkable property.
- **Synthetic/non-sensitive filler content: resolved workshop-wide, but with a real gap** — see
  Finding 1, below.
- **Empirical threshold across all 6 modules: only partially resolved.** The Instructional Designer
  persona makes an important distinction the prior triage missed: only Module 01 has an actual
  numeric pass/fail bar on the *measured value*. Modules 02, 03, 05, and 06 deliberately gate on
  *procedure and completeness* (run-count caps, trial counts, honest reporting) rather than a result
  threshold — a defensible design choice (it avoids incentivizing a "good" result over an honest
  one), but it means the prior finding's letter was met while its spirit wasn't fully addressed, and
  neither this doc nor the prior triage acknowledged that distinction. **Not treated as a defect to
  fix** — flagged here as a design choice that should be stated explicitly rather than left to look
  like an oversight.

## Cross-cutting theme: Module 04 (Compaction Mechanics) has two independent, real problems

**Flagged independently by AI/ML Practitioner (methodology) and Security-Conscious Reviewer
(content safety)** — different angles, same module, both real:

1. **The gate doesn't isolate what it claims to.** Comparing a pre-compaction control probe against
   a post-compaction probe conflates compaction-specific loss with ordinary long-context/positional
   decay (the same effect Modules 02/03 already measure) — without a third arm (same distance,
   compaction *not* triggered), the reported delta can't distinguish "compaction ate it" from "it
   was just far away."
2. **The synthetic-content rule has a loophole here.** The workshop-wide guardrail bans real/
   sensitive content in "haystack/filler" text, but Module 04's own exercise description says to
   reach the compaction trigger by "filling context with real or synthetic tool output" — a learner
   could satisfy the letter of the module by running real tool calls against real repos/configs to
   hit the token count fast, pulling real paths or credential-shaped data into a reviewed transcript.

## Other high-confidence findings

**Skeptical Critic: Module 03's own title and repeated references use a banned phrase.**
`docs/brand.md` explicitly bans "at scale" unless the content proves the scale — yet the module is
literally named "Context Rot at Scale," and nothing about a "≥3 points spanning a 4x range" sweep
is an at-scale claim by any normal reading. This is the exact pattern the rule exists to catch,
caught in this workshop's own arc-defining module name.

**AI/ML Practitioner: two more real methodology gaps.**
- Modules 02/03's sweeps have no repeat-trial minimum the way Module 04 does, despite the
  workshop-wide "Gate tiers" section requiring every module to acknowledge measurement variance — at
  the ≤20-run cap, some cells could resolve to a single trial, reported as "accuracy" when it isn't
  a rate at n=1.
- Module 03 says to hold "a depth already characterized in Module 02" fixed, without specifying
  *which* depth — if Module 02's own result is flat (a validly allowed outcome), there's no
  principled choice, and picking wrong could mask a real length effect.

**Instructional Designer: two fresh findings.**
- Module 05's stated hard prerequisite ("Module 02, 03, *and* 04") is stronger than its own
  justifying text, which only requires *one* prior baseline to target.
- Module 02's first learning objective (predict the curve shape before running it) isn't checked by
  either gate tier.

**Security-Conscious Reviewer: the cost cap isn't tied to a safety habit.**
The ≤20-invocation guardrail controls cost, but nothing requires a human checkpoint before a sweep
fans out — a learner could read the number as license to script a fully unattended loop up to that
count.

## Single-persona findings

**Developer Evangelist**
- The README's pitch is buried under mechanism/jargon (Coachgremlin, "empirical gate," "conceptual
  check") before any concrete symptom or number appears.
- `docs/brand.md` models an exact illustrative phrasing ("Recall dropped to 40% at depth 50%") that
  the README itself never uses — the flagship pitch page is all vibe, zero number, for a workshop
  whose whole thesis is "show the number."
- No fast "if this happened to you, start here" signpost from symptom to module; that map only
  exists one click deep in `modules/README.md`.

**Technical Writer**
- README.md says "empirical gate"/"conceptual check"; every other file says "empirical tier"/
  "conceptual tier" — the reader's first exposure uses different names than the rest of the
  workshop.
- "needle-in-a-haystack" vs. "needle-in-haystack" used inconsistently, including within the same
  file (Module 02, README.md).
- "Synthesis capstone" vs. "Synthesis Capstone" capitalization inconsistent across files.
- Confirmed clean: no em dashes anywhere in scope, all cross-references resolve correctly, all 6
  modules follow the identical 8-part template.

**End-User/Learner**
- The scripted-non-interactive-harness skill gap the design-doc pass flagged is *named* in every
  module now but not *taught* — correctly deferred to Coachgremlin's content-authoring pass, not a
  skeleton-stage defect, but worth tracking so it doesn't get silently dropped when that pass starts.
- The cost guardrail gives a run-count cap but no ballpark dollar/wall-clock estimate, so it's
  honest but not yet reassuring.

## Prioritized action list

1. **Fix Module 04's confound** — add a stated control arm (or explicitly scope the claim down to
   what the two-probe design can actually support) so the gate's conclusion matches what it measures.
2. **Close the Module 04 synthetic-content loophole** — extend the guardrail's synthetic/non-
   sensitive rule explicitly to cover tool-output filler, not just haystack text.
3. **Rename Module 03** away from the banned phrase "at scale" and update every cross-reference.
4. **Add repeat-trial guidance to Modules 02/03**, and **specify the depth-carry-forward rule** for
   Module 03.
5. **Fix Module 05's overstated prerequisite** (one of 02/03/04, not all three).
6. **Add a human-checkpoint line to the cost guardrail** so the ≤20 cap reads as a safety habit, not
   just a cost control.
7. **Fix terminology**: "empirical tier"/"conceptual tier" consistently (including README.md),
   "needle-in-a-haystack" spelling, "Synthesis capstone" capitalization.
8. **Add one hedged illustrative number to the README** matching `brand.md`'s own modeled phrasing.
9. **Add a gate check for Module 02's first learning objective** (the pre-registered prediction).
10. Soften Module 01's `±10%` tolerance to match the same "not yet validated" hedge the cost cap
    already uses, per the Skeptical Critic's finding.

## Not actioned by this report

The scripted-harness-sweep skill gap and the cost estimate's lack of a dollar/time ballpark are
correctly deferred to Coachgremlin's content-authoring pass — the skeleton's job is to state the
gate's shape, not teach the skill or run a real estimate before any script exists.
