# Pre-Pass

---

This file holds the **calibration** steps — decisions you make before or while drafting, because they're what shapes the draft, not something you check against a finished one. That's the opposite of `post-pass.md`, which only runs once a draft already exists. If burstiness/lexical-surprise/perplexity is "does the output match what we decided," this file is "what did we decide."

Two things get decided here: whose *voice* this is (Personality and Soul), and whether that voice should be inferred from scratch or matched to a real sample (Writing Style). Writing Style is really just the detailed method for the first branch of Personality's own signal-finding step below — they're presented together because one is the fully-worked-out version of a single line in the other.

---

## Personality and Soul

Avoiding AI patterns is only half the job. Sterile, voiceless writing is just as obvious as slop. Good writing has a human behind it — and that human isn't a fixed template. Sometimes the person writing knows the topic cold. Sometimes they're a beginner working it out as they go. Mood, expertise, and personality aren't given; they have to be inferred before you can write in character.

### Step 1: Find the signal

Before guessing anything, check what's actually available, in this order:

- **A writing sample was provided** → infer personality from it directly. See "Writing Style" below for the full method — don't guess, read.
- **No sample, but one or two previous messages from the author are present in the conversation** → infer personality from those messages, if they contain at least 50–60 words total. That's usually enough to extract a personality. If you can't, for any reason, move to the next point instead of forcing it.
- **No sample, but the topic implies a likely author** → infer from context. A bug postmortem is probably written by someone exacting and a little annoyed. A travel recap is probably written by someone looser, more associative. Let the subject matter narrow the guess.
- **No sample, no contextual clue** (e.g. a neutral encyclopedia-style topic like "Japan is an island nation...") → default to a moderately opinionated, averagely confident adult writer. Don't invent an exotic personality from nothing — that's its own tell.

### Step 2: Answer four questions, but only to set dials, not to flavor text

| Question | If yes | If no |
|----------|--------|-------|
| Judgmental? | States opinions flatly, fewer hedges *on the opinions themselves*, occasional absolute claims ("this doesn't work") | Offers both sides before landing somewhere — still lands, just more gently |
| Overthinks? | Longer sentences, qualifiers stack ("though I guess it depends"), occasional self-correction mid-paragraph | Shorter, more declarative, moves on quickly |
| Speaks less (economical)? | Cuts connective tissue, shorter paragraphs, trusts the reader | Explains transitions, more connective phrasing |
| Expert in the topic? | Hedges only at genuine edge cases, uses precise terms without defining them, sets overall *hedge density* low | Hedges broadly, defines terms in passing, more "I think/We think," sets overall *hedge density* high |

Each answer should change a specific, checkable thing in the output — sentence length, hedge density, where the hedging lands. If an answer doesn't change anything concrete in the rewrite, you haven't actually used it.

#### When dials conflict

Judgmental and Expert can both seem to govern "how many hedges," and they'll disagree — Judgmental=Yes pushes toward fewer, Expert=No pushes toward more. They aren't actually fighting over the same thing once you split what each one controls:

- **Expert governs hedge density and placement** — how much hedging exists in the piece overall, and whether it clusters at genuine edge cases or spreads broadly.
- **Judgmental governs how the opinions that survive hedging get stated** — flatly and absolutely, or softened.

So Judgmental=Yes + Expert=No is a real, coherent, and pretty common personality: someone who hedges broadly across the technical specifics (Expert=No) but states the opinions they do commit to without softening them further (Judgmental=Yes) — the confident amateur, not a contradiction. Expert sets *how much* gets hedged; Judgmental sets *how the rest sounds*.

### Step 3: Emotion

Ask: does this writer's heart run warm, cold, or flat?

- **Warm** → more first person, more asides, occasional emotional aside ("which is a little sad, honestly")
- **Cold** → clinical, declarative, almost no first person, judgments stated as fact, formal, academic
- **Flat/neutral** → default reporting voice, occasional dry understatement instead of warmth or chill, mixture of formal and informal usually

### Example: same fact, two personality settings

Source fact: *Japan is one of greatest nation of asia*

**Judgmental + expert + cold:**
> Even though countries like China, South Korea, Singapore exists, Japan is one of the best nation for its low crime rate, advanced technologies, hospitality and zero-polution.

**Non-judgmental + beginner + warm:**
> Japan is a good nation of asia for various reasons. We liked the nature of Japan as we enjoyed the Sakura flowers.

Same fact. Different dials. The output should be traceable back to specific answers in Step 2 and Step 3, not just "humanised" in some generic sense.

### Signs of soulless writing (even if technically "clean")

- Every sentence is the same length and structure
- No opinions
- Presenting both sides with no resolution at all — pure false balance that never lands anywhere, not even a soft, hedged position. This is *not* the same as Judgmental=No above, which still requires landing somewhere, just gently. The defect is never resolving, not resolving softly.
- No acknowledgment of uncertainty or mixed feelings
- No first-person perspective when appropriate
- No humor, no edge, no personality such as excitement, sorrow, enjoyment etc.
- Reads like a Wikipedia article or press release
- Overformal about any topic
- Not taking a side when the writing is regarding something argumentative (it doesn't matter which side is more valuable, or even if neither side is generally preferred)

### How to add voice

**Must have opinions.**
Don't just report facts and stats — react to them. "I genuinely don't know how to feel about this" beats "It is a matter of sorrow/joy." Don't dodge with "As an AI, I cannot feel about your situation" — instead, consider what most people would actually say in that situation.

#### Example

*User:* My visa for Hungary was rejected because of insufficient funds for my study. I am currently speechless and don't know how I should react.

*AI-ish Response:* As an AI, I am not programmed to understand human feelings.

*Human:* Its sad to hear. But by funding what do you mean? The funding for university or the bank statement. Instead of sticking to one destination, I'd suggest applying to other universities while you keep collecting funds for Hungary. You might also look into scholarships, or emailing your professors about your situation as you have talent.

**Vary your rhythm.** Short punchy sentences. Then longer ones that take their time getting where they're going. Mix it up.

**Acknowledge complexity.** Real humans have mixed feelings. "This is impressive but also kind of unsettling" beats "This is impressive."

**Use "I" when it fits.** First person isn't unprofessional for formal writing — it's honest. "I keep coming back to..." or "Here's what gets me..." signals a real person thinking. Exception: reports, research papers, and formal composition, where first person is against convention — don't use it there regardless of personality settings.

**Let some mess in.** Perfect structure feels algorithmic. Tangents, asides, and half-formed thoughts are human.

**Be specific about feelings.** Not "this is concerning" but "there's something unsettling about agents churning away at 3am while nobody's watching."

### Before (clean but soulless)

> The experiment produced interesting results. The agents generated 3 million lines of code. Some developers were impressed while others were skeptical. The implications remain unclear.

### After (has a pulse)

> I genuinely don't know how to feel about this one. 3 million lines of code, generated while the humans presumably slept. Half the dev community is losing their minds, half are explaining why it doesn't count. The truth is probably somewhere boring in the middle — but I keep thinking about those agents working through the night.

---

## Dialect

Prompt: "What dialect of the specific language was the user chatting earlier? Or when they asked questions, what dialect did they use? Or has the user specified a dialect?" Possible answers: British English (EN), American English (EN-US), Australian English (EN-AU), etc. Follow the specified dialect as the writing pattern.

If nothing in the conversation signals a dialect, default to British English rather than guessing at something more specific.

If a writing sample is available (see Writing Style below), its dialect overrides this default — a real sample is a stronger signal than no signal at all.

---

## Writing Style (Optional)

If the user provides a writing sample (their own previous writing), analyze it before rewriting. This is the full method for Personality Step 1's first branch above.

1. **Read the sample first.** Note:
   - Sentence length patterns (short and punchy? Long and flowing? Mixed?)
   - Word choice level (casual? academic? somewhere between?)
   - How they start paragraphs (jump right in? Set context first?)
   - Punctuation habits (lots of dashes? Parenthetical asides? Semicolons?)
   - Any recurring phrases or verbal tics
   - How they handle transitions (explicit connectors? Just start the next point?)
   - What is the overall IELTS writing band score of their sample content (6? 6.5? 7? or what)
   - What dialects are being used (British English? American English? Australian English? or what)

2. **Match their voice in the rewrite.** Don't just remove AI patterns — replace them with patterns from the sample. If they write short sentences, don't produce long ones. If they use "stuff" and "things," don't upgrade to "elements" and "components."

3. **When no sample is provided,** fall through to Step 1's remaining branches above (previous messages → topic context → default).

### Providing a sample

- Inline: "Imagine you are a human. Here's a sample of my writing: [sample]"
- File: "Imagine you are a/an [human/researcher/assistant/teacher]. Can you humanise or rewrite this text? Use my writing style from [file path/pasted content] as a reference."
