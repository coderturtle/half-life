# Session Log: Half-Life

## 2026-07-07 - Initial scaffold

Project scaffolded as **factory-output**. Purpose: Empirical, harness-driven workshop teaching why LLMs degrade over long context (context rot, compaction, lost-in-the-middle) via scripted Claude Code CLI/SDK experiments with real pass/fail scoring.

### Decisions Made

- Classification: factory-output
- Owner: coderturtle
- Vault mutation: not allowed by default
- Promotion target: none

### Next Actions

- Define brief and first phase plan
- Add first implementation
- Record initial decisions

## 2026-07-07 - Naming pass + workshop design draft

Concept interview held first (interview-me skill) to nail down: empirical/measurable checker
(confirmed — like Rust's compiler, but for context behavior), audience (agent-literate practitioners
+ LLM-app builders), harness-first method (Claude Code CLI/SDK scripted runs, not raw API calls),
standalone-but-complementary relationship to `terminal-velocity`.

Naming pass run: 10 candidates generated, all GitHub-slug-checked under `coderturtle` before
presenting. Human picked **Half-Life** from a 4-option shortlist. Full rename executed and
authorized: local dir, GitHub repo (`gh repo rename`), git remote, `.hekton/project.yaml`,
repo-local mind-palace mirror, and the live vault card at
`~/vaults/hekton-mind-palace/20-projects/factory-output/half-life`.

Real research pass run (WebSearch) for the canonical-curriculum-anchor step: confirmed Lost in the
Middle (Liu et al.), Kamradt's needle-in-a-haystack methodology, Chroma's Context Rot report (July
2025), Anthropic's "Effective context engineering for AI agents" (Sept 2025), and Claude Code's real
`/compact` mechanism all as live, real sources. Drafted `docs/workshop-design.md`: 6-module arc,
harness-first empirical method, two-tier gate design (empirical measurement + Coachgremlin
conceptual layer).

### Decisions Made

- See `docs/decisions.md` 2026-07-07 entries (naming, design doc).

### Next Actions

- Run first Workshop Review Panel pass against `docs/workshop-design.md`.
- Build module skeleton + branding layer incorporating Review Panel findings.
- Stand up build-log/Pages site skeleton.

## 2026-07-07 - Workshop Review Panel pass + triaged fixes

Ran the Workshop Review Panel (7 parallel personas) against `docs/workshop-design.md`. All seven
returned distinct findings. Two cross-persona agreements: the empirical-tier gate is only concrete
for 2 of 6 modules, and no cost/scope bound exists for scripted parameter-sweep exercises. Resolved
one factual dispute during review (fetched Chroma's report directly — confirmed "coherent input
degrades attention more than shuffled" is accurate as written) and one citation error (verified via
`gh api` that the needle-in-a-haystack link pointed at an Arize fork, not Kamradt's original).
Full report: `docs/review-panel/2026-07-07-initial-design.md`.

User triaged: applied the cheap text-only fixes now (citation, etymology softening, `/compact`
citation correction, terminology consistency, naming-rationale addition); deferred the structural
findings (gate concreteness across all 6 modules, cost bound, capstone distinctness) to the Task 4
module-skeleton pass. See `docs/decisions.md`'s 2026-07-07 entries for the full itemized list.

### Next Actions

- Build module/deliverables skeleton + branding layer, addressing the deferred structural findings.
- Stand up build-log/Pages site skeleton.

## 2026-07-08 - Module skeleton + brand layer

Built the full module skeleton (`modules/README.md` arc overview + 6 module READMEs, 8-part
template each: question, arc position, learning objectives, exercise-material pointer, required
gate, takeaway, stop condition, skeleton-only banner), addressing every structural finding deferred
from the Review Panel pass: a concrete empirical-tier threshold per module (all 6, not just 2), a
workshop-wide cost/scope guardrail (`modules/README.md`'s "Cost & scope guardrails" section),
Module 02's gate explicitly treating a flat/null curve as valid, and the capstone's gate requiring
reuse of Module 04's or Module 05's methodology rather than repeating an earlier sweep pattern.

Built `docs/brand.md` (adapted from `borrow-native`), carrying forward this workshop's own
Skeptical Critic and AI/ML Practitioner findings as permanent hard rules (never state an unverified
numeric threshold, never claim a canonical finding "will reproduce" without hedging). Split learner-
facing `README.md` from internal `docs/maintainers.md`. Wired `scripts/check-brand-lint.sh` into the
pre-push hook (warn-only), adapted from `borrow-native`'s script.

Brand lint caught a real em-dash habit across all 6 module files and `README.md` on first run;
fixed via bulk substitution, then manually corrected two spots where the automated fix left a line
starting with `- ` that would have rendered as an accidental markdown bullet list on GitHub. Brand
lint clean after the fix.

### Decisions Made

- See `docs/decisions.md`'s 2026-07-08 entry.

### Next Actions

- Stand up the build-log/Pages site skeleton (Task 5, the Workshop Gremlin's last roster item).
- Content-building (Coachgremlin, one module at a time) is next but outside this Gremlin's own
  Completion Condition.

## 2026-07-08 - Module-skeleton Review Panel re-run + fixes

User asked whether the Review Panel had actually critiqued the new module skeleton/brand/README
content (it hadn't - only the earlier design-doc-only pass existed). Re-ran the full 7-persona
panel against this new content, per the panel's own "significant content revision" re-run trigger.

This pass caught real methodology bugs, not just polish: two personas independently found distinct
problems with Module 04's compaction gate (a confound between compaction-specific loss and ordinary
long-context decay, and a synthetic-content loophole in its own exercise text), and the Skeptical
Critic caught the workshop's own banned phrase ("at scale") sitting in Module 03's title. Full
report: `docs/review-panel/2026-07-08-module-skeleton.md`.

User chose to apply all 10 findings now. Fixed: Module 04's confound (added a third control arm) and
content loophole, renamed Module 03 ("Length-Driven Context Rot"), repeat-trial guidance for
Modules 02/03, a concrete depth-selection rule for Module 03, Module 05's overstated prerequisite,
a human-checkpoint requirement on the cost cap, a gate check for Module 02's prediction objective,
Module 01's tolerance hedge, terminology consistency, and one real cited number added to the README.
Verified all internal markdown links still resolve after the module 03 directory rename. Brand lint
clean throughout.

### Decisions Made

- See `docs/decisions.md`'s second 2026-07-08 entry.

### Next Actions

- Stand up the build-log/Pages site skeleton (Task 5, the Workshop Gremlin's last roster item).
