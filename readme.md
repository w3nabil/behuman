# Become Human

**"Project Become Human", coded "S-NAB-052", A writing skill that strips AI "tells" out of generated text and puts a real voice back in.**

![Version](https://img.shields.io/badge/version-0.2.1-blue) ![License](https://img.shields.io/badge/license-CC%20BY%204.0-lightgrey)

---

## What it is

Become Human is an [Agent Skill](https://github.com/anthropics/skills) — a `SKILL.md` plus a handful of reference files — that rewrites AI-generated text so it reads like a person wrote it. It doesn't just strip obvious tells like em dashes and "Certainly!". It reconstructs the writing: varied sentence entropy, a deliberately chosen personality, dialect consistency, and two dedicated self-critique passes before anything reaches you.

Internally the project frames this around the **Penta-State Probabilistic Model (PSPM)** — a five-state scale (True / Partially True / Undecided / Partially False / False) for how confidently a piece of text reads as human-written. See [Known limitations](#known-limitations) for where that part of the project currently stands.

## Features

- **Pattern removal** — over two dozen documented AI-writing tells across six categories (content, language & grammar, style, communication, filler & hedging, and citation handling), building on the pattern catalogue from [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing).
- **Personality dial system** — four yes/no questions (Judgmental? Overthinks? Economical? Expert in the topic?) plus a Warm / Cold / Flat emotional register. Every stylistic choice in the output should trace back to a specific answer, not just a vague "sound more human" nudge.
- **Voice calibration** — hand it a writing sample and it matches your sentence length, word choice, and punctuation habits instead of imposing a default style.
- **Dialect handling** — defaults to British English when there's no signal to go on, and reads context (or the conversation itself) to switch to American, Australian, or another regional dialect.
- **Burstiness calibration** — deliberately varies sentence *entropy*, not just length, so the writing doesn't sit at one predictable complexity level for a whole passage.
- **Lexical surprise + perplexity audit passes** — two closing passes that isolate the most "predictable" sentences and the most obviously AI-picked words, and rework only those.
- **PSPM confidence read-out** — an optional closing label (e.g. "High confidence that it is human-written") summarizing how the rewrite landed.

## How it works

1. Read the input, and the writing sample if one's provided.
2. Scan for AI patterns against `pattern.md`.
3. Rewrite, preserving meaning and matching the intended tone.
4. Set the personality dials and emotional register.
5. Run the burstiness, lexical surprise, and perplexity audit passes.
6. Self-critique — "what makes this obviously AI-generated?" — and revise.
7. Present the final rewrite, with an optional summary of changes and a PSPM read.

## Installation

No dependencies, no build step — it's a folder. Where it goes depends on the surface:

| Surface | Location |
|---|---|
| **Claude Code** — personal (all projects) | `~/.claude/skills/become-human/` |
| **Claude Code** — project (shared via git) | `.claude/skills/become-human/` at the repo root |
| **Claude Desktop** | Same as Claude Code: `~/.claude/skills/become-human/` |
| **claude.ai** | Settings → Features → upload the folder as a `.zip` |
| **Claude API** | Upload via the [Skills API](https://docs.claude.com) (`/v1/skills`) — shared workspace-wide |
| **OpenCode / other agents** | It's a plain `SKILL.md` folder — check that tool's own skill-loading docs for where custom skills go |

```bash
# Claude Code, personal skill, latest release
curl -L -o become-human.zip https://github.com/w3nabil/become-human/archive/refs/tags/v0.2.1.zip
unzip become-human.zip -d ~/.claude/skills/
mv ~/.claude/skills/become-human-0.2.1 ~/.claude/skills/become-human
```

Front matter declares `allowed-tools: Read, Write, Edit, Grep, Glob, AskUserQuestion, DeepResearch` — grant those if your setup asks.

## Usage

Just ask, in plain language:

> "Remove the AI-signs from this [paste text / file path]"

> "Imagine you are a human. Here's a sample of my writing for voice matching: [sample]. Now rewrite this: [text]"

> "Can you humanise this text? Use my writing style from [file] as a reference."

No sample needed. Without one, Become Human falls back to a moderately opinionated, averagely confident default voice rather than guessing at something exotic.

### Example

**Before:**
> AI-assisted coding serves as an enduring testament to the transformative potential of large language models, marking a pivotal moment in the evolution of software development... The tool serves as a catalyst. The assistant functions as a partner. The system stands as a foundation for innovation.

**After:**
> AI coding assistants can make you faster at the boring parts. Not everything. Definitely not architecture.
>
> They're great at boilerplate: config files, test scaffolding, repetitive refactors. They're also great at sounding right while being wrong. I've accepted suggestions that compiled, passed lint, and still missed the point because I stopped paying attention.

## File structure

```
become-human/
├── SKILL.md            # Core instructions, personality system, process
├── pattern.md          # The full AI-pattern catalogue (6 categories)
├── pspm.md             # PSPM formulas and scoring procedure
├── evidence.md         # The 17-question checklist PSPM scores against
├── reference.md        # Sources
└── writing-thinking/   # Tone-variant notes (conversational, formal, learning)
```

## Known limitations

A showcase shouldn't hide the rough edges, so here's where things stand honestly:

- **PSPM's confidence score is experimental.** A term it depends on ("accuracy threshold") isn't defined anywhere in the current files, one of its sub-calculations (Undecided Aspect Ratios) isn't actually read by the final formula, and the tie-breaking rule for the strong-evidence checklist can discard the partial-evidence signal entirely rather than weighing it in. Treat the PSPM label as a qualitative flourish for now rather than a precise metric — the pattern-removal and personality-dial work is what's doing the real lifting on output quality.
- **The "always take a side" instruction** (under Signs of Soulless Writing) means the skill will state an opinion on argumentative topics even when neutrality is genuinely the right call. Worth knowing before pointing it at sensitive or purely informational content.
- **PSPM's theoretical basis is a preprint**, not yet a peer-reviewed or independently validated method — worth treating accordingly until that changes.

## Credits

- AI-writing pattern catalogue builds on [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) and WikiProject AI Cleanup.
- Builds on [blader/humanizer](https://github.com/blader/humanizer) (MIT).
- PSPM: N. Islam, "Penta-State Probabilistic Model (PSPM)," Oct. 2025. [doi:10.31224/5566](https://doi.org/10.31224/5566)

## License

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — see `licence` in this repo, and `changelog.md` for release notes.

---

*Maintained by Nabil ([@w3nabil](https://github.com/w3nabil))*
