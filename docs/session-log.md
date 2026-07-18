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

## 2026-07-08 - Build-log/Pages site (Task 5)

Stood up `site/`: Astro adapted directly from `borrow-native`'s starter (Content Layer API reading
`docs/build-log/` in place, `base`-aware links throughout, same Tailwind/typography tokens). Wrote
Half-Life's own `index.astro` guide content (two-gate explanation, real-research framing, runbook)
rather than reusing Borrow Native's Rust-specific copy. New favicon (½ glyph, matching the
decay-rate theme). `.github/workflows/deploy-pages.yml`, `workflow_dispatch`-only per the Human
Gate.

Locally validated: `npm install` (4 inherited vulnerabilities from the starter, same as
`terminal-velocity`/`borrow-native`'s own first install, not yet triaged - RISK-0002), `npm run
build` clean, `astro check` clean (0 errors/warnings/hints), and confirmed directly in the built
HTML that every internal link carries the `/half-life/` base correctly.

Wrote the first build-log entry deliberately (not generated from session logs): covers this run's
two real methodology findings from the module-skeleton Review Panel pass (Module 04's confound, the
banned-phrase module rename) as the actual story of this run, matching `borrow-native`'s own
build-log discipline.

This closes the Workshop Gremlin's own Completion Condition - all five roster steps (scaffold,
naming, first review pass, module skeleton/branding, build-log/Pages site) are now done. Content-
building (Coachgremlin) and the human-confirmed first live deploy are explicitly outside this
Gremlin's stop condition.

### Decisions Made

- See `docs/decisions.md`'s third 2026-07-08 entry.

### Next Actions

- Get a human to enable GitHub Pages and trigger the first real `workflow_dispatch` deploy
  (RISK-0003).
- Triage the 4 inherited npm vulnerabilities before that first real deploy (RISK-0002).
- Coachgremlin content-building begins with Module 01, per the existing plan.

## 2026-07-08 - RISK-0002 triage (npm vulnerabilities)

Checked exploitability directly rather than assuming: grepped `site/src/` for `define:vars` and
server-island usage (none), confirmed `astro.config.mjs` sets `output: "static"` (no
server-rendering runtime), confirmed no user-controlled input reaches slot names or spread props
anywhere in this codebase, and confirmed the GitHub Actions workflow only runs `npm run build`
(never `astro dev`, so the Windows-dev-server esbuild advisory doesn't apply either). None of the 5
advisories are reachable given this site's actual configuration.

Attempted the real fix anyway on a new branch (`agent/claude/vuln-triage`): `npm audit fix --force`
upgrades cleanly to `astro@7.0.6` with 0 vulnerabilities, but `npm run build` then failed twice -
first on the removed legacy content-config path (mechanical fix: move `src/content/config.ts` to
`src/content.config.ts`), then on `@astrojs/tailwind` itself, which throws
`Cannot read properties of undefined (reading 'postcss')` on Astro 7. Astro moved away from
bundling a Tailwind integration in favor of Tailwind's own Vite plugin - this isn't a drop-in
version bump, it's a real integration migration. Reverted the upgrade attempt back to the exact
state merged in Task 5 (confirmed via `git diff` against HEAD showing zero net change), reinstalled
original dependencies, and re-validated `npm run build`/`astro check` both clean.

Closed RISK-0002 as an accepted risk with the verified reasoning above, rather than forcing a
Tailwind-migration project into what should be a bounded triage task. Recorded the known upgrade
path in `docs/risks.md` for whenever `site/`'s dependency stack gets touched deliberately.

### Decisions Made

- See `docs/decisions.md`'s 2026-07-08 RISK-0002 entry.

### Next Actions

- Get a human to enable GitHub Pages and trigger the first real `workflow_dispatch` deploy
  (RISK-0003) - the only remaining open item before this workshop's scaffolding phase is fully done.

---

## 2026-07-18 - Fixed a fully-broken custom domain, found while building coderturtle.io's Workshops page

**Agent:** Claude

### What changed

- Building a Workshops listing page on `coderturtle.io` surfaced a real, live bug: `curl` against
  `half-life.coderturtle.io` returned 404 on every path (plain HTTP too, not a cert issue), and the
  `coderturtle.github.io/half-life/` fallback 301-redirected back into the same 404.
- Root cause: GitHub Pages' `cname`/domain-verification were already live and `"verified"` (set at
  some point since 2026-07-08's entries, never recorded), but `site/astro.config.mjs` still had
  `base: "/half-life/"` and no `site/public/CNAME` existed — the repo-side cutover was never done.
- Fixed on branch `agent/claude/custom-domain-cutover`: `astro.config.mjs` (`site`/`base` to the
  domain root), new `site/public/CNAME`, `.github/workflows/deploy-pages.yml`'s stale comment
  corrected. `npm run build` reconfirmed clean, `dist/CNAME` present.
- Also confirmed via `gh run list`: this repo has **never had a deploy run at all** — RISK-0003's
  "get a human to trigger the first deploy" item was never actually done, despite Pages/domain
  config existing. Still open, see Next Actions.

### Decisions Made

See `docs/decisions.md`'s 2026-07-18 entry.

### Risks

No new RISK entry — RISK-0003 (first deploy still pending) stays open, now with a corrected config
underneath it.

### Next Actions

Review/merge the cutover PR, then trigger the genuinely-first `workflow_dispatch` deploy and
confirm the site is actually live via direct `curl`, not just a green workflow run.

### Validation

- Real `curl` checks (custom domain, plain HTTP, project-page redirect target) confirmed the break
  before fixing.
- `npm run build` clean; `dist/CNAME` = `half-life.coderturtle.io`.
- `gh run list --workflow=deploy-pages.yml` — empty, confirming no deploy has ever run.

### Mind-palace updated

No — not yet authorised this session.
---

## Session: Fixed a live, fully-broken custom domain; first deploy this repo has ever had

**Date:** 2026-07-18 20:59

### What Changed

half-life.coderturtle.io was 404ing on every path, and this repo had never had a single deploy run at all - found while building coderturtle.io's Workshops page. Fixed astro.config.mjs/public/CNAME, triggered and confirmed the first real deploy ever, enabled the push trigger, closed RISK-0003

### Decisions

See docs/decisions.md's 2026-07-18 entry

### Assumptions

None new

### Risks

RISK-0003 closed

### Next Actions

- [ ] Coachgremlin content-building begins: Module 01 (Context Window Mechanics)
