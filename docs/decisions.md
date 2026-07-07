# Decisions: Half-Life

## ADR Log

| Date | Decision | Rationale |
|---|---|---|
| 2026-07-07 | Initial scaffold as factory-output | Empirical, harness-driven workshop teaching why LLMs degrade over long context (context rot, compaction, lost-in-the-middle) via scripted Claude Code CLI/SDK experiments with real pass/fail scoring. |
| 2026-07-07 | Named **Half-Life** (renamed from working title `context-workshop`) | Human-picked from candidates (Half-Life, Lost in the Middle, Context Rot, Needle Native), all GitHub-slug-checked under `coderturtle` first. "Half-Life" fits the empirical/measurable framing better than a literary or pure-jargon name. Full rename (repo, remote, `.hekton/project.yaml`, repo-local mirror, live vault card) explicitly authorized. |
| 2026-07-07 | Drafted `docs/workshop-design.md`: 6-module arc (Window Mechanics → Positional Bias → Context Rot at Scale → Compaction Mechanics → Mitigations → Synthesis capstone) | Anchored to real canonical material researched this session: Lost in the Middle (Liu et al. 2023/2024), Kamradt's needle-in-a-haystack methodology, Chroma's Context Rot report (2025), Anthropic's "Effective context engineering for AI agents" (2025), and Claude Code's real `/compact` mechanism. Teaching method is harness-first empirical measurement (scripted Claude Code CLI/SDK runs, never raw API scripts), with a two-tier gate (empirical measurement primary, Coachgremlin conceptual tier secondary) — this workshop's equivalent of `borrow-native`'s compiler/clippy gate, built from scratch since this subject has no existing objective-checker tool. |
