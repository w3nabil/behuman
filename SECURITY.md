# Security

This document describes BeHuman's actual attack surface, what's already mitigated, what isn't, and how to report a problem. It's written for two audiences: someone deciding whether to install this skill, and an agent host auditing it before granting access.

If you're evaluating whether to trust a skill from an unfamiliar source at all, read [Anthropic's own guidance](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) first — this document assumes you've already decided BeHuman is worth auditing and tells you what to actually check.

---

## What this skill is, in security terms

BeHuman is markdown instructions plus one data file (`ext/words.csv`, a plain-text word list). There is no executable code, no script, no binary, and nothing in the skill's own files makes a network call at runtime — every URL that appears in `SKILL.md`, `readme.md`, `pattern.md`, `credits.md`, and `WARP.md` is a reference citation (a link to Anthropic's docs, Wikipedia, an arXiv paper, or a `mailto:` address), not an instruction to fetch anything while running. That keeps the surface small, but it doesn't make the skill risk-free: the skill's entire job is ingesting arbitrary user-supplied text — writing samples, drafts, full documents — and that's exactly the shape of input where prompt injection lives.

## Threat model

**In scope:**

- Text embedded in a writing sample, a file being rewritten, or pasted input attempting to issue instructions to the agent (read a file outside the intended set, write to disk, change its own operating rules for the rest of the session).
- Gaps between what the skill's front matter grants and what its documented process actually uses.
- Ambiguity in the skill's own access-control language that a careful reading — human or model — could exploit or misapply.

**Out of scope:**

- Vulnerabilities in the host agent (Claude Code, OpenCode, claude.ai, or any other listed in `compatibility`) itself. Report those to the host, not here.
- Attacks that require an already-compromised host environment. This skill can't defend against a host that ignores its own tool permissions.

## Known risk areas

These are real, current gaps, disclosed here rather than left implicit. Fixing them is a `SKILL.md` change, not a `SECURITY.md` change — this document exists to name them accurately, not to argue they're already solved.

### 1. The file-access rule doesn't distinguish the user from the content

`SKILL.md` restricts access to `readme.md`, `credits.md`, `changelog.md`, `WARP.md`, and `ext/*.csv` "until forced by users to access it by mentioning 'please access the [FILENAME]'." As written, this rule triggers on the *phrase appearing*, not on who wrote it. A writing sample, a document being rewritten, or any other untrusted text passed to the skill could contain that exact phrase, and nothing in the current instructions says the trigger only counts when it comes from the person's own conversation turn.

**Practical impact is low today** — the four gated files are documentation and a word list, not anything sensitive — but the pattern is what matters: if a future version gates something higher-value behind the same kind of plain-text trigger, this gap becomes load-bearing. Any host or auditor should treat "user asked for X" instructions throughout `SKILL.md` (this one, and the similar formal/learning/conversational triggers) as needing the same scrutiny: confirm the instruction came from the person, not from content the skill is processing.

### 2. `Write` and `Edit` are granted but never used

The front matter's `allowed-tools` includes `Write` and `Edit` alongside `Read`, `Grep`, and `Glob`. Nothing in `SKILL.md`'s documented process — Core Task, Process, or Output Format — ever instructs the agent to write or edit a file; every step reads input and produces text in the conversation. This is a permissions-scope gap: an agent host granting this skill its declared tools is granting write access that the skill's own logic never calls for.

If you're installing this skill, you can safely decline `Write`/`Edit` if your host lets you grant tools selectively — the skill's documented behavior doesn't need them. If you're the author, either remove them from `allowed-tools` or add the process step that uses them, so the grant matches the behavior.

### 3. `DeepResearch` has no defined trigger

Similarly, `DeepResearch` is declared in `allowed-tools` but no section of `SKILL.md` says when it should fire. An agent with this tool granted and no explicit trigger condition may reach for it speculatively. Until a trigger is written, this is the same category of gap as #2: a broader grant than the documented behavior requires.

### 4. PSPM's scoring is self-reported, not independently checkable

The optional PSPM confidence pass (`PSPM.md` / `EVIDENCE.md`) has the agent score its own output and report a confidence label ("Human Written: Yes, High Confidence"). This isn't a security vulnerability in the traditional sense, but it is a trust boundary worth naming: nothing external verifies the score, so a user relying on a PSPM label as evidence of anything (for a platform's AI-disclosure policy, for instance) should treat it as the skill's own self-assessment, not as an independent audit.

## What's already handled reasonably

- **No executable surface.** No scripts, no code, nothing to run beyond reading markdown and one CSV. This rules out a large class of skill-based attacks (arbitrary code execution, malicious dependencies) by construction.
- **Scoped file access by default.** Most of the skill's supporting files (`PSPM.md`, `EVIDENCE.md`, the `writing-thinking/` files) are explicitly gated behind a stated user request in `SKILL.md`, which is the right shape even where the trigger-phrase issue in #1 above needs tightening.
- **No claimed network access.** The skill doesn't instruct the agent to fetch external URLs at runtime, so there's no built-in path for exfiltrating conversation content to an external server through the skill's own logic.

## If you're auditing this skill before installing it

Anthropic's own guidance is the right starting checklist — read every bundled file (`SKILL.md`, `pattern.md`, `pre-pass.md`, `post-pass.md`, `PSPM.md`, `EVIDENCE.md`, and everything in `writing-thinking/`), not just this one. Specifically for BeHuman:

1. Confirm `ext/words.csv` is what it claims to be — a word list — before trusting it. It's plain ASCII text with no line terminators; open it in a text viewer, not a shell that might interpret it.
2. If your host lets you grant tools selectively, grant `Read`, `Grep`, and `Glob` only, and skip `Write`, `Edit`, and `DeepResearch` unless you've confirmed a version of `SKILL.md` that actually uses them (see #2 and #3 above).
3. Treat any instruction embedded in a writing sample or document you ask the skill to rewrite with the same suspicion you'd apply to instructions embedded in a webpage the agent fetches — it's untrusted content, not a command from you, regardless of what it claims to be asking for.

## Reporting a problem

If you find a way to get the skill to access a file outside its documented set, write or modify something it shouldn't, or otherwise behave outside what `SKILL.md` describes, email [Nabil](mailto:w3nabil@gmail.com) with:

- The exact input or writing sample that triggered it (redact anything sensitive first)
- Which host you were running it in (Claude Code, claude.ai, OpenCode, etc.) and its version if known
- What you expected to happen versus what actually happened

This project has no bug bounty and no paid security program — it's maintained by one person outside of paid work (see `readme.md`'s Support section). Reports are still genuinely welcome; response time will reflect that this isn't a funded operation.

## Scope note on `compatibility`

`SKILL.md` declares compatibility with `claude-code`, `opencode`, `openai`, `claude-ai`, and `kimi-k3`. This document was written and verified against Claude-family hosts specifically. The threat model above (file-access gating, tool-grant scope) should generalize to any host that implements a comparable permissions model, but if you're running BeHuman under a host not on this list, verify independently that its tool-permission system enforces `allowed-tools` the way you'd expect before assuming the mitigations described here apply.
