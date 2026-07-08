# Brand / Style Layer: Half-Life

> The only place this workshop's personality lives. `README.md` and, once built, `site/`'s layout
> and `astro.config.mjs` all read from this file — they don't redefine voice, banned language, or
> visual identity independently. Adapted from `borrow-native/docs/brand.md`, itself adapted from
> `terminal-velocity/docs/brand.md` and blog-factory-lab's `templates/brand-style-layer-template.md`.

## Site identity

**Name:** Half-Life
**Tagline:** Don't take the paper's word for it — measure your own model's context decay, then prove your fix actually works.
**Parent brand:** Hekton
**Slug:** `half-life`

The tagline leads with the empirical hook (reproduce it yourself, on your own tool) rather than the
subject-list pitch ("context windows and their effect on LLM behavior...") — the same fix
`borrow-native`'s Developer Evangelist finding made permanent there. This workshop's own Review
Panel found the same issue: the sharpest line in the design doc was buried mid-document instead of
leading the pitch (`docs/review-panel/2026-07-07-initial-design.md`).

## Tone and voice

**Core voice:** A careful experimenter, not a hype account. Specific, measured, shows the actual
number rather than asserting the vibe. Treats the reader as someone who already ships with LLMs
daily — the thing assumed unfamiliar is the research and the discipline of measuring it themselves,
not the tools.

**Tone rules:**
- Prefer a reported number over an adjective. "Recall dropped to 40% at depth 50%" beats "recall
  got much worse."
- Any claim about what a phenomenon will do on the learner's own model/harness must be hedged
  unless a real dry run has confirmed it — **direct fix for this workshop's own Skeptical Critic
  and AI/ML Practitioner findings** (the design doc's "reproduction... almost unchanged" and
  "structurally equivalent to a compiler" both overclaimed before a single module existed). State
  the null result as a real, valid outcome, not a failure of the exercise.
- Never assert a specific numeric threshold ("N points," "95% context utilization") without a
  named source or a stated placeholder — this workshop's own Review Panel caught both kinds in the
  design doc directly.
- First person for build-log entries. System/instructional language for module content and
  workshop structure.
- Admit uncertainty directly rather than smoothing over it.
- Never frame a measured LLM behavior as "the model being dumb" or "broken" — this workshop's whole
  thesis is that context rot is a well-studied, measurable, explicable phenomenon, not a mysterious
  failure. Mockery undercuts the pitch as much as hype does.

## Hard rules

- **No em dash characters.** Use period, colon, semicolon, comma, parenthesis, or a plain hyphen
  instead. (Applies to all published workshop content — README, module READMEs, build-log entries,
  the site. Design/planning docs under `docs/` are working documents and are exempt.)
- No AI-slop openers ("In today's fast-paced world...", "It's important to note...").
- No unqualified efficacy superlatives ("game-changing," "revolutionary," "10x," "unlock your
  potential") — direct fix for this workshop's own Skeptical Critic findings against the design
  docs.
- No engagement bait, fake scarcity, or "one weird trick" framing.
- **Subject-specific:** never state a specific token count, percentage, or trigger threshold as
  fact without a named, checkable source (a paper, an official doc, or "measured directly in
  `runs/<date>-<module>/`"). This workshop's own design doc shipped with an unverifiable "~95%"
  compaction-trigger figure before its first Review Panel pass caught it — the fix is a permanent
  voice rule, not a one-time edit.
- **Subject-specific:** never claim a canonical finding (Lost in the Middle, Chroma's Context Rot
  report) "will reproduce" on the learner's own harness without hedging that frontier models may
  have attenuated the effect since the source was published — state the null result as a real,
  defensible outcome every time reproduction is invoked.

## Banned phrases

Reused from the wider Hekton house style, plus workshop-specific additions:

- delve, tapestry, unlock, seamless, game-changing, revolutionize, transform your workflow,
  supercharge, effortlessly, cutting-edge, thought leader
- "in today's fast-paced world," "it's important to note," "at scale" (unless the content proves
  the scale)
- Workshop-specific: "master the art of," "in this comprehensive guide," "unlock your potential,"
  "10x your skills," "the model is dumb," "the model is broken," "AI hallucinates because" (a
  hand-wave that skips the actual mechanism this workshop exists to teach)

## Visual identity

Inherit `terminal-velocity`/`borrow-native`'s Astro starter tokens rather than invent a new
palette, once the site is built: `--accent`, `ink`/`paper` Tailwind tokens, the `.post-body`
typography rhythm, "no section dividers, whitespace only."

| Element | Direction |
|---|---|
| Overall mood | Clean technical lab notebook. Not a marketing landing page. |
| Colour approach | Dark-on-light default; restrained palette; dark mode optional later |
| Typography | Crisp, generous whitespace, readable code blocks and data tables (this workshop reports real numbers more often than code diffs — legible tables matter as much as syntax highlighting did for `borrow-native`) |
| Imagery | Artifact-led: measured curves/tables, terminal sessions, real harness output — not stock photos, decorative AI art, or invented illustrative charts not backed by a real run |
| Decoration | No neon AI aesthetic, no hero banners, no gradient-mesh backgrounds |

## Gremlin and factory language rules

- Coachgremlin and the Workshop Gremlin are real, documented agents with concrete responsibilities
  (`~/hekton/gremlins/`) — reference them plainly when explaining how the workshop works, don't
  decorate every heading with gremlin language, and don't assume a learner already knows what a
  "Gremlin" is without a one-line explanation the first time the term appears in learner-facing
  copy.
- A module README is a production artifact: plain. A build-log entry can be funny where the actual
  events were funny.

## Anti-goals

- Not an AI-hype funnel or a marketing page for Hekton.
- Not a research-paper reading group — the papers are anchors, not the deliverable; the deliverable
  is the learner's own measurement.
- Not a place to publish unverified efficacy or reproduction claims — every claim about what a
  phenomenon does on the learner's own harness gets the hedge treatment above until there's a real
  dry run's evidence behind it.
- Not overrun with gremlin language to the point of reading childish.
- Not mockery of LLM behavior ("lol it forgot again") — the thesis is that this is measurable and
  explicable, not a punchline.

## Application map

| Artifact | Reads |
|---|---|
| `README.md` | Title + tagline |
| `site/` (once built) | Tone, hard rules, banned phrases, visual identity |
| Module READMEs | Tone, hard rules, banned phrases, subject-specific hedge rules |
| Build-log entries | Tone and voice rules (first person, honest null results, no hype) |

## [TBD]: items for later

- [ ] Exact accent colour token (once site is built)
- [ ] Favicon / wordmark treatment
- [ ] Dark mode colour tokens
- [ ] A results-table/chart visual convention for reporting real measured data consistently across modules
