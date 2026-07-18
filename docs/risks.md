# Risks: Half-Life

## Risk Register

Machine-readable risk state lives in `.hekton/risk-register.yaml`. Keep this
Markdown file as the human-readable explanation of material risks and mitigations.

| ID | Date | Risk | Impact | Likelihood | Mitigation | Status |
|---|---|---|---|---|---|---|
| RISK-0001 | 2026-07-07 | Initial governance baseline needs first human/agent review | Medium | Medium | Run governance preflight and end-session review during the first material session | Open |
| RISK-0002 | 2026-07-08 | `site/`'s adapted Astro starter carries 4 inherited npm vulnerabilities (3 low, 1 high - Astro/esbuild advisories affecting the pinned `^5.0.0` range; same starter `terminal-velocity`/`borrow-native` also inherited) | Low - triaged 2026-07-08, see below | Certain (present on first `npm install`) | **Triaged and accepted, not fixed.** See rationale below. Re-open if `output` mode ever changes from `"static"`. | Closed |
| RISK-0003 | 2026-07-08 | GitHub Actions deploy workflow (`workflow_dispatch`-only) and the site build itself are locally validated (`npm run build`, `astro check` both clean, base-aware links confirmed in built HTML) but the actual Actions run is unproven until a human triggers it | Medium | Certain until triggered | Triggered 2026-07-18 (`workflow_dispatch`, run 29643482348) — build+deploy both green, confirmed live via `curl` against `half-life.coderturtle.io` returning real rendered content, not just a green run. Same session also fixed a real, live custom-domain 404 that predated this (see `docs/decisions.md`'s 2026-07-18 entry) — the deploy succeeding alone wouldn't have caught that, since the domain config was the separate broken piece. | Closed |

## RISK-0002 triage detail (2026-07-08)

`npm audit` reports 4 vulnerabilities (3 low, 1 high) against `astro@^5.0.0`, `@astrojs/mdx`, and
`@astrojs/tailwind`, all resolving to five Astro GHSAs plus one esbuild GHSA:

- Astro: XSS via `define:vars` incomplete `</script>` sanitization, reflected XSS via unescaped
  slot name, XSS via unescaped attribute names in spread props, server-island encrypted-parameter
  replay, host-header SSRF in prerendered error pages.
- esbuild: arbitrary file read via the dev server, Windows-only.

**Checked directly against this site's actual code, not assumed inapplicable:**
`grep -rn "define:vars\|server:island" site/src/` returns nothing - this site never uses either
feature. `astro.config.mjs` sets `output: "static"` - there is no server-rendering runtime for the
server-island/SSRF advisories to apply to. All slot names and spread props in this codebase are
static, written by the maintainer, not derived from user input at any point - there's no attacker-
controlled data path into the two remaining XSS advisories. The esbuild advisory is scoped to
`astro dev`'s dev server on Windows; the GitHub Actions workflow only ever runs `npm run build` on
`ubuntu-latest`, never `astro dev`.

**Attempted the fix anyway, reverted:** `npm audit fix --force` upgrades to `astro@7.0.6` cleanly
(0 vulnerabilities after), but breaks two things that need a real migration, not a version bump:
the content collection must move from `src/content/config.ts` to `src/content.config.ts` (an
Astro 6 removal, mechanical), and `@astrojs/tailwind` fails outright on Astro 7
(`Cannot read properties of undefined (reading 'postcss')`) - Astro moved away from bundling a
Tailwind integration in favor of Tailwind's own Vite plugin, so this isn't a drop-in bump.

**Decision:** accept the risk as-is rather than force a Tailwind-migration project into what should
be a bounded triage. None of the 5 findings are reachable given this site's actual configuration.
The upgrade path is known and cheap to revisit (this exact triage) whenever there's a real reason
to touch `site/`'s dependency stack - e.g. before a future move off `output: "static"`, or when
Tailwind v4's Vite-plugin migration gets done as its own deliberate piece of work rather than a
side effect of a CVE count.
