# Post-Pass

---

This file holds the **post-pass** checks — instructions that only make sense once a full draft already exists, not things you scan for while reading raw text. `pattern.md` is a line-level pattern list: read a sentence, spot an em dash or a hedge, fix it, move to the next sentence. Everything here needs the whole picture instead — checking entropy variance across a paragraph, or asking whether a specific word was the single most predictable choice, only means something once the draft is finished and settled.

Run `pattern.md` first. Run this file last, on the result.

**Order inside this file matters too.** Burstiness Calibration runs first, then Lexical Surprise, then Perplexity Audit — in that order, every time. Restructuring a sentence changes which words end up sitting next to which other words, so checking word choice before the structure is finalized just means re-checking it later anyway, or worse, not catching that a later merge introduced something clunky. See the worked example under Burstiness Calibration; it's the reason for the order, not a preference.

---

## Burstiness Calibration

Burstiness describes how much a piece of writing's surprisal — how hard the next word is to predict — swings from one sentence to the next. It's a different question from *how surprising is this text overall* (that's perplexity); burstiness asks how unevenly that surprise is spread out. Sentence length plays a part too: a longer sentence has more room to include something unpredictable, but length alone doesn't guarantee it — a long sentence can stay completely predictable, and a short one can land a genuine surprise.

Before looking at burstiness directly, it helps to see surprisal on its own. Compare these two sentences:

**Common phrasing:**
> The book was in the bag.

**Rare phrasing:**
> The book was in the shower.

*Observe:* Neither sentence is illogical — a book really could end up in a shower, say if `the author was reading it before showering and left it there`. The difference isn't logic, it's frequency: across huge amounts of text, "book" and "bag" appear together constantly, while "book" and "shower" almost never do. Measuring both with GPT-2-medium gives roughly `~5 bits` of surprisal for "bag", and `~7 bits` for "shower" — the second sentence needs more bits because the model has to work harder to arrive at a word it didn't expect.

Now let's look at when and how much burstiness is needed. Burstiness is sparse — it does not require much across a paragraph. **Less** surprisal overall, concentrated into occasional spikes, is what reads as human; surprisal on every sentence reads as exhausting, and surprisal on none of them reads as AI-flat. A useful default: roughly one real surprisal spike in every 4–5 sentences, not one per sentence.

### What raises surprisal

Each of these raises surprisal through a different mechanism, not by being interchangeable instances of "unpredictable":

- **Rare or technical vocabulary** raises surprisal by *word rarity* — the model has simply seen the word less often, in any context, so its baseline probability is lower before the sentence even sets up a slot for it.
- **A specific number, date, or named entity** raises it by *information the prior sentence gave no basis to predict* — a vague reference like "a while later" is compatible with almost any specific answer, so "a while later" costs little, while "eleven years later" forces the model to have guessed one value out of many.
- **An embedded or subordinate clause** raises it *structurally* — it inserts a fact mid-sentence that the main clause's grammar didn't require, so the model has to absorb new content in a slot it expected to be a simple continuation.
- **An unexpected causal or comparative link** raises it *relationally* — the surprise isn't in any single word but in the connection between two ideas the previous sentence hadn't pointed toward.

Knowing which mechanism is in play matters for revision: if a sentence still reads as flat after adding a rare word, the fix might be structural (add a clause) rather than lexical (find a rarer synonym), because the flatness could be coming from predictable *sentence shape*, not predictable *word choice*.

### Sentence Length vs. Surprisal

Human writing does vary in sentence length — a sentence rarely lands within a word or two of the one before it. A passage might run 5 words, then 16, then 7, with no steady interval. AI writing tends to flatten this too, with each sentence landing close to the same length: 7 words, then 7, then 7 again.

But length variation is not the same thing as surprisal variation, even though the two often show up together. Compare:

**Short:**
> I am the Hunter.

**Long:**
> Ever heard of the Guild of Hunters, those who are the best at their craft, I am one of them.

The second sentence is three times the length of the first, but neither one is hard to predict; both stay easy to guess word-to-word once you're a few words in. This is a length swing without a surprisal swing — proof that varying length alone doesn't produce burstiness. A passage can jump between short and long sentences all through and still read as flat if nothing in it is actually hard to guess. Length gives surprisal *room* to vary; it doesn't cause the variation by itself. Real burstiness needs both: length that moves unpredictably, *and* at least some of those sentences landing a genuine surprisal spike.

**Without Burstiness (flat):**
> In a small laboratory with ageing equipment and limited funding, a scientist from a developing nation worked tirelessly to pursue her research. She had never attended a prestigious university and lacked access to the advanced education available in wealthier countries, yet she refused to abandon her ambitions. Financial burdens weighed heavily on her; some months, she struggled to pay basic expenses while trying to keep her experiments alive. Despite repeated setbacks, rejected proposals, and scarce resources, she continued learning from books, public papers, and experience.

**With Burstiness:**
> Mythical 02B, a small laboratory without modern equipment and limited funding. A scientist named Alexis, from the Philippines, worked tirelessly to pursue her research without caring about the burden. She had never attended a university in her country. Advanced education about AI and LLM is widely available in Europe and the United States of America but not in her country yet. Despite these challenges, she refused to abandon her ambitions without having a dead-end fight. Financial burdens weighed heavily on her. For 8 months, she struggled to pay basic expenses while trying to keep her experiments alive, as they're her last hope. According to her, a scientist does not need food but only hunger for knowledge. For her funding and knowledge, she tried contacting professors of various universities, including Harvard, Chalmers, and EURECOM, but her research proposals were rejected every time she shared them. With scarce resources, she continued learning from books. Aside from that, she reads public papers and online books and sometimes watches YouTube learning videos to learn upcoming concepts for her work.

**Changes Noticed:**

- The opener is a genuine burst: "Mythical 02B, a small laboratory without modern equipment and limited funding" is a sentence fragment, not a full declarative sentence, and it front-loads an odd, specific word ("Mythical") the reader has no basis to predict. That's real, content-driven surprisal.
- Sentence length swings much harder than in the flat version — a four-word fragment sits a few sentences away from a forty-word sentence, closer to the unpredictable range the doc's length section describes than to the earlier drafts managed.
- Not every addition is the same kind of surprisal, though. "Alexis," "the Philippines," and "8 months" are named-entity spikes — genuinely hard to predict on first mention. But "Harvard, Chalmers, and EURECOM" is a list: the first name is a real spike, and each name after it costs less surprisal than the one before, because by the second name the reader already expects a list of universities. A four-item enumeration reads as one spike stretched out, not four.
- The "does not need food but only hunger for knowledge" line is memorable, but memorability and surprisal aren't the same axis. It's an epigram — dense in a stylistic, quotable sense — rather than statistically unpredictable in the frequency sense this section defines surprisal by. Worth knowing the difference, since reaching for aphorisms is its own recognizable move, not a substitute for genuine surprisal.
- Net effect: this version fixes the repeated-template problem the previous draft had (no construction repeats itself three times), and the opening fragment plus the length range are real, checkable improvements. The proper-noun list and the epigram are where the paragraph is doing something else — more ornate, more "written" — rather than more surprisal-variant in the sense the rest of this document defines.

#### Over-corrected (a new failure mode)

The ratio rule above — one real spike per 4–5 sentences — is easy to overshoot once a writer notices flatness and starts hunting for it everywhere. Applied to the same premise, over-correction looks like this:

> The lab, officially designated 02B, ran on a lapsed grant. She kept going anyway. Her funding had evaporated eight months prior, alongside three rejected proposals from Harvard, MIT, and a Swedish consortium she'd cold-emailed at 2 a.m. She read anyway. The isolation was total, unbroken by any institutional acknowledgment that her work existed. She wrote anyway.

*Observe:* Every dense sentence is followed by a short one, every short one by a dense one — plain, spike, plain, spike, plain, spike, with no exception across the whole paragraph. That regularity is itself detectable: a reader (or a model) doesn't need to know *what* comes next, only that it will alternate, which is exactly the kind of learnable schedule the earlier section on timing-unpredictability warns against. The repeated "\_\_\_ anyway" close on the short sentences compounds it — three short sentences sharing one construction is a template, the same failure the original draft's example had before it was rebuilt. Fixing flatness by scheduling spikes trades one mechanical pattern for another; the goal was never *more* spikes, it was spikes that land where the content has something to justify them, at an interval too irregular to predict.

*Fix:* break the schedule itself, not just the sentences riding on it. Vary which sentence gets the spike (sometimes the second in a pair, sometimes the fourth), vary how the short sentences close (don't let "anyway" carry all three), and let at least one plain sentence sit next to another plain sentence somewhere in the paragraph, so no reader or model can predict the next beat from the last one.

### Run this before Lexical Surprise, never after

Word choice is a *local* optimization: the best word for a slot depends on everything around that slot — the words before it, the clause structure, what the sentence has already committed to grammatically. Change any of that context and the optimization has to be redone, because "best" was only ever best relative to a specific surroundings that no longer exists. Restructuring a sentence for burstiness — merging clauses, splitting one sentence into two, moving a fact from the end to the middle — changes exactly that surrounding context. A word choice that was the best option for the original sentence shape can become clunky the moment that shape changes around it.

This is why order isn't a stylistic preference but a dependency: Lexical Surprise has to run on the *settled* structure, or it ends up polishing word choices in a sentence that gets rebuilt a moment later — and nothing catches the seam, because the word-level pass already finished and has no way to know its work was invalidated.

---

## Lexical Surprise

Definition:

> `Commonly used words` means the word is in the Oxford 5000 word list — a graded pedagogical list correlated with frequency, not a direct probability ranking, so "on the list" is a useful proxy for common but not a guarantee of the single most probable word.
> `Rarely/uncommon used words` means any word not on that list.

Problem: AI uses the best and/or rarely used verb and/or words for writing to express.

Solution: Before doing the verb and word choice, AI should:

- Check if the word and/or verb is used for every usage.
- Check if the word and/or verb is perfect for the specific dialect and context.
- Check if the word has the highest-probability and/or most-guessed.

### Example (Not overly used words, but best choice for LLM)

**Before:**
> The company uses an ingenious security system to protect user data.

**After:**
> The company uses an advanced security system to protect user data.

**Observe:** The word `ingenious` explains the sentence perfectly but the problem is it is almost never used and/or rarely used. We replaced the word with `advanced` (and fixed the article before) because `advanced` is more often used.

### Example 2 (Not overly used words, but best choice for LLM)

**Before:**
> The wood looks too brittle.

**After:**
> The wood looks too fragile.

### Example (Commonly used words, but best choice for LLM)

**Before and After:**
> The issue has been resolved, and a fix has been implemented.

**Observe:** The words of this sentence is commonly and widely used, no changes needed.

### Example (Idiom and/or Phrases remains as it is)

**Before:**
> Not only did the boyfriend and girlfriend undertake a date, but they also elected to split the bill. Their conversation broke the ice and consolidated their relationship.

**After:**
> Not only did the boyfriend and girlfriend plan a date, but they also decided to split the bill. Their conversation broke the ice and deepened their relationship.

**Observe:** At first we modified `undertake` with `plan` and `elected` with `decided` which makes more sense for the context. On the second line, `consolidated` was reworked with `deepened`. Phrase `Not only..... but also` and idiom `broke the ice` remained intact.

---

**Prompt:** *Which verbs and/or adjectives are used? Make a list of them then observe if they are uncommon and/or rare and then modify them (2 to 3 words maximum) using the 2nd or 3rd word choice if the words are common for the sentence. If not common, what is the most commonly used word? let's substitute them with only the commonly used words.*

---

Run this **after** Burstiness Calibration, on the settled sentence structure — never before. See the examples above for why.

### The failure mode: surprising isn't the same as better

The prompt above has no stopping condition. Taken literally, it pushes toward whichever word is least predictable, with nothing to stop that from turning into purple prose. A surprising word only earns its place if a reader doesn't have to pause on it. If the replacement calls attention to itself *as* a word choice, that's overcorrection — go back one step, not two.

#### Example: financial reporting

Baseline: *The company's profits fell sharply last quarter.*

- "Fell" is the predictable choice.
- **Overcorrected:** *The company's profits cratered catastrophically last quarter.* Less predictable, but now the sentence sounds like it's trying — "cratered" and "catastrophically" are both doing the same job.
- **Correct fix:** *The company's profits dropped last quarter.* One step less predictable than "fell." Doesn't call attention to itself.

#### Example: physical description

Baseline: *The wind was very strong during the storm.*

- "Strong" is the predictable choice.
- **Overcorrected:** *The wind was apocalyptic during the storm.* Technically surprising. Also wildly out of proportion for a plain descriptive sentence — it announces itself as a word choice instead of just describing wind.
- **Correct fix:** *The wind was fierce during the storm.* One step less predictable. Reads as description, not as a flex.

Two different domains, same failure mode: treating "less predictable" as the whole goal, instead of "least predictable while still invisible," overshoots every time.

---

## Perplexity Audit

Prompt: *"Which 2 or 3 sentences in this text are the most predictable — where each word follows almost inevitably from the last?"* Rewrite only those sentences, introducing one unexpected but natural word or structural break each.

This is the true final pass. It needs the whole text, after Burstiness Calibration and Lexical Surprise have already run, because "most predictable" is a judgment about what's left over once everything else has already been fixed.

### Diagnose before you rewrite

Flagging the flattest sentences isn't enough on its own — a sentence can be flat for three different reasons, and the fix depends on which one applies:

- **Flat from syntax** — plain subject-verb-object, no subordination, nothing for a reader (or a model) to absorb mid-sentence. *The team finished the project on time.* Fix structurally: add a clause, not a word. *The team, working through two rounds of delayed approvals, finished the project on time.* This is Burstiness Calibration's tool, reapplied here because the earlier pass didn't happen to catch this sentence.
- **Flat from vocabulary** — every word is high-frequency, nothing costs the model any real probability mass. *He was very happy with the results.* Fix with a one-step swap, the same move as the Lexical Surprise section above: *He was surprised by the results* (if true to the content) rather than reaching for "elated" or "euphoric," which trips the same overcorrection failure mode covered there.
- **Flat from missing content** — grammatically sound, nothing wrong with it, but there's no actual information a reader couldn't have guessed. *This is an important issue that needs attention.* Neither structure nor vocabulary is the problem here; the sentence has nothing to say. Add a real detail — a number, a name, a specific consequence — or cut it. No rewrite trick fixes an empty sentence.

Check these in order: syntax, then vocabulary, then content. A sentence can look vocabulary-flat when it's actually syntax-flat underneath — if a word swap doesn't fix the flatness, the sentence needed a clause, not a rarer synonym. Ruling out syntax first stops a cycle of swapping synonyms on a sentence that never had anywhere for a word to be surprising, no matter which word filled the slot.

### Expect short sentences to score worse, independent of content

Later words in a sentence are generally easier to predict than earlier ones, since each additional word narrows the possibilities for what follows. That means a short sentence has less room to settle into predictability and will often score as more "flat" on this kind of measure than a longer sentence would, even when the short sentence's content is perfectly fine. Before treating a flagged short sentence as the real problem, check whether it's genuinely flat in the sense the diagnostic above describes, or whether it's just short. If a short sentence is doing real work — landing a point, closing a beat — its length may be the reason it scores poorly here, not a sign it needs rewriting.

### Sentences are not independent — check the whole-text number

A language model conditions each word on everything before it, including prior sentences. Rewriting a flagged sentence changes the conditioning for every sentence after it. This is why fixing the bottom 2-3 sentences can raise the predictability of sentences you never touched — the flagged list will usually look different after every edit. That's the mechanism working, not a sign the edit failed.

Because of this, judge an edit by overall perplexity across the full text, not by whether the one sentence you targeted individually cleared some bar. A targeted sentence can genuinely improve — score higher, less predictable, than it did before — and still rank last in its own draft, simply because the rest of the paragraph improved faster around it. Don't revert a working edit because of where it ranks relative to its neighbours; check where it sits relative to its own earlier score instead.

Set a stopping point before starting — a target overall-perplexity number, or a fixed number of edit attempts — so this doesn't turn into an open-ended chase for a lower number that may not exist within a small edit budget.

If a late edit meaningfully changes the flatness ranking of a sentence already fixed under Burstiness Calibration or Lexical Surprise, don't loop back and re-run those passes on it. One bounded exception: if the newly-flattest sentence is flat enough to be the single worst sentence in the whole text, it may get one more diagnostic pass using the check above — otherwise, accept the small resulting inconsistency rather than reopening earlier work indefinitely.

### Don't spread the fix evenly — concentrate it

The instinct is to take each of the 2-3 flagged sentences and give it roughly the same treatment: a careful rewrite, a bit of structural break, applied consistently across all of them. Tested against a real human-written sample, this turned out to be the wrong shape.

A six-sentence human-written self-introduction scored 54.77 overall perplexity on the measurement setup used for this comparison (results are relative to the model and tokenizer used, not a fixed target). Five of its sentences were completely ordinary and low-scoring — plain, predictable, unremarkable ("Hello!", "My name is Fiie Rhexis.", "You may call me Fiie."). The overall number was carried almost entirely by one sentence spiking to 157.00, on a slightly odd, faintly non-native phrasing ("I am good at conducting various tasks like talking to people behalf of you") that reads like something nobody planned — not an engineered structural break, just a rough patch a real person produced without trying to.

Compare that to an evenly-edited AI paragraph that reached a similar overall number (55.55) by giving deliberate, careful treatment to several sentences at once — inversion, fronting, added detail, spread across the flagged set. The aggregate score landed in the same range, but the texture was opposite: uniform moderate effort across many sentences, instead of ordinary writing with one genuine rough spot. Matching the number doesn't mean matching the thing the number is a proxy for.

So: leave most of the paragraph plain. Don't rework every flagged sentence — pick the one or two spots that can plausibly carry a real spike, and let the rest of the text sit at normal, unremarkable predictability. A spike that reads as unplanned (an odd but plausible word or phrasing, the kind of rough patch a distracted or informal writer produces without meaning to) does more for the overall number, and for actually sounding human, than a moderate, evenly-applied lift across several carefully constructed sentences.

### The failure mode: the fix should be invisible on a second read

If you can point to exactly which word or clause was added to break the predictability, the seam is still showing. The goal isn't "technically less predictable" — it's a sentence that lands differently without a reader being able to say why.

#### Example: overcorrection vs. a light touch

Baseline: *The meeting ran long, and by the end everyone was tired. We made a decision, but nobody was fully happy with it. That's just how compromise works.*

The third sentence is the predictable one — it's a stock closing line.

- **Overcorrected:** *We landed somewhere. Nobody loved it, which is sort of the whole point of splitting a difference nobody asked to split.* Technically less predictable. Also reads as try-hard — a sentence performing its own cleverness instead of closing the thought.
- **Correct fix:** *That's just how most compromises work* One word. The predictability breaks without announcing that it's breaking anything.

#### Example: instructional text needs a different bar

Baseline instruction: *Restart the router and wait thirty seconds.*

This sentence is maximally predictable — every word follows from the last — and that's usually fine in instructions. Breaking it can actively hurt:

- **Overcorrected:** *Restart the router, then let thirty seconds of silence do their quiet work.* Less predictable. Also slower to parse into an action, which is the one thing an instruction can't afford to be.
- **Correct fix, if a fix is even needed:** *Restart the router. Wait thirty seconds and you are ready to go.* The fragment breaks the rhythm and quietly corrects a common mistake — people often wait less than they should — without costing any clarity.

In instructional or technical text, breaking predictability must never cost actionability. If the "more natural" version takes longer to turn into an action than the original did, revert. Predictability is sometimes the correct choice, not a defect to fix.
