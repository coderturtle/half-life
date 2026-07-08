# Risks: Half-Life

## Risk Register

Machine-readable risk state lives in `.hekton/risk-register.yaml`. Keep this
Markdown file as the human-readable explanation of material risks and mitigations.

| ID | Date | Risk | Impact | Likelihood | Mitigation | Status |
|---|---|---|---|---|---|---|
| RISK-0001 | 2026-07-07 | Initial governance baseline needs first human/agent review | Medium | Medium | Run governance preflight and end-session review during the first material session | Open |
| RISK-0002 | 2026-07-08 | `site/`'s adapted Astro starter carries 4 inherited npm vulnerabilities (3 low, 1 high - Astro/esbuild advisories affecting the pinned `^5.0.0` range; same starter `terminal-velocity`/`borrow-native` also inherited) | Low (static-only build, no dev server exposed in production; `npm audit fix --force` requires an Astro major upgrade) | Certain (present on first `npm install`) | Triage before the first real Pages deploy: either accept as static-build-safe with a documented rationale, or take the breaking `astro@7` upgrade and re-validate `npm run build`/`astro check` | Open |
| RISK-0003 | 2026-07-08 | GitHub Actions deploy workflow (`workflow_dispatch`-only) and the site build itself are locally validated (`npm run build`, `astro check` both clean, base-aware links confirmed in built HTML) but the actual Actions run is unproven until a human triggers it | Medium | Certain until triggered | Human triggers `workflow_dispatch` after enabling Pages (Settings > Pages > Source: GitHub Actions); confirm the real deploy succeeds, not just the local build | Open |
