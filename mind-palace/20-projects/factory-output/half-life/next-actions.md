# Next Actions: Half-Life

## Immediate

- [x] Stand up the build-log/Pages site skeleton (Astro-on-Pages, reusing `terminal-velocity`/
      `borrow-native`'s pipeline) — done 2026-07-08, locally validated (`npm run build` and
      `astro check` both clean, base-aware links confirmed in built HTML). This closes the
      Workshop Gremlin's own Completion Condition — all five roster steps are now done.
- [ ] Get a human to enable GitHub Pages (Settings > Pages > Source: GitHub Actions) and trigger
      the first real `workflow_dispatch` deploy — the Actions run itself is still unproven until
      triggered. See RISK-0003 in `docs/risks.md`.
- [ ] Triage the 4 inherited npm vulnerabilities in `site/`'s Astro starter before that first real
      deploy (RISK-0002 in `docs/risks.md`).
- [ ] Register in the mind-palace Gremlin Registry once vault mutation is authorised for that
      purpose.

## This Week

- Coachgremlin content-building begins: Module 01 (Context Window Mechanics) is the natural first
  real dry run, since it has no cost/scope-guardrail concerns the way Modules 02-03 do.

## Later

- Re-run the Workshop Review Panel once real module content exists (per its own cadence: every 2-3
  modules of real content, not per module).
- Author Modules 02-06 (Coachgremlin's job, one at a time) — each must produce a real dry run
  evidencing whether the empirical-tier/conceptual-tier gate split actually works in practice, an
  open bet this design pass explicitly left untested.
