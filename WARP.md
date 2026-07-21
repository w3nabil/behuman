# WARP.md

This repo contains **BeHuman**, an [Agent Skill](https://github.com/anthropics/skills) that rewrites AI-generated text so it reads like a person wrote it. This file is project-level context for Warp's agent when working *inside this repo* — it is not the skill itself. The actual instructions live in `SKILL.md` and its supporting files.

## What's in this repo

- `SKILL.md` — core instructions: pattern removal, dialect handling, the read-order and gating rules for every other file. Personality and voice calibration live in `pre-pass.md`, not here.
- `pattern.md` — the AI-writing pattern catalogue (five categories: content, language & grammar, style, communication, filler & hedging).
- `pre-pass.md` — personality, dialect, and writing-sample calibration, done *before* drafting.
- `post-pass.md` — Burstiness Calibration, Lexical Surprise, Perplexity Audit, run *after* a draft exists, strictly in that order.
- `PSPM.md` / `EVIDENCE.md` — PSPM's scoring formulas and the 17-question checklist it scores against. Optional; read only if the user asks for PSPM scoring.
- `writing-thinking/` — register-specific notes. `formal.md` is fully substantive (109 lines of actual guidance). `learning.md` and `conversational.md` both have a complete gating rule and trigger examples but little to no actual writing guidance underneath — `learning.md` has no content section at all, and `conversational.md` sets up one heading ("Tone Rework") and cuts off mid-sentence with nothing under it. See Known limitations in `readme.md`.
- `readme.md`, `changelog.md`, `credits.md` — not read by the skill during normal operation as of 0.3.0 (this was a deliberate change to cut token usage). Read them yourself when you need repo context; the skill itself only opens them if a user explicitly names one.
- `ext/` — repo related stuffs, not needed for SKILL to run.

## Using BeHuman as a Warp Skill

Warp has its own Skills system, separate from this file. To make BeHuman invocable inside Warp, copy this folder into a skills directory Warp scans:

```bash
.agents/skills/behuman/     # project-level, recommended — also picked up by Cursor, Codex, Gemini, Copilot, etc.
~/.agents/skills/behuman/   # global, all projects
```

No reformatting needed. This repo is already a plain `SKILL.md` folder, which is what Warp's Skills system expects.

## Conventions when editing files in this repo

- Match the existing style: numbered lists for procedural steps; `### Example:` headers with **Before/After** blockquotes for worked examples (see the worked examples in `pre-pass.md` and the Burstiness Calibration section in `post-pass.md`).
- Default dialect is British English unless a specific file's content signals otherwise.
- Filenames are case-sensitive on disk: `PSPM.md` and `EVIDENCE.md` are both uppercase; `readme.md`, `changelog.md`, `credits.md`, `pattern.md`, `pre-pass.md`, and `post-pass.md` are lowercase. Get the case wrong and a case-sensitive lookup on Linux will simply fail to find the file.
- Some looseness in the skill's own voice is intentional (first-person asides, informal tone). Before "fixing" any phrasing that looks like a typo, check whether it's actually still there — a previous version of this file flagged specific typos that have since been corrected in the skill files themselves; don't assume a past note about wording still applies without rereading the current text.
- `readme.md`'s Known Limitations section previously referenced an "always take a side" rule under a "Signs of Soulless Writing" heading. That heading and rule do not exist in the current `pattern.md` or anywhere else in this repo — it appears to have been removed or renamed in a past version without the corresponding limitation note being removed. If you're touching `pattern.md` or `readme.md`, confirm with the author whether this limitation still applies before carrying it forward again.
- Known unresolved issues — PSPM's scoring formula, the `conversational.md` stub, the version mismatch above — are tracked in `readme.md`'s Known Limitations section. If you're editing something else and notice one of these, flag it separately rather than quietly patching it inline.
