# Known AI Patterns

This file contains various known AI and/or LLM patterns that make writing look like obvious AI-generated text. For other instructions, please consider looking at `./writing-thinking/formal.md` or `./writing-thinking/conversational.md`. Some sections here contain special signals; for your understanding, the meanings are given below:

|       Signal      | Meaning                                                                                                        |
|:-----------------:|----------------------------------------------------------------------------------------------------------------|
|   Words to watch  | The rule is applied when the following and/or similar word/s is/are present in a sentence and/or paragraph     |
| Sentence to watch | The rule is applied when the following and/or similar sentence/s is/are present in a sentence and/or paragraph |
|   Signs to watch  | The rule is applied when the following and/or similar sign/s is/are present in a sentence and/or paragraph     |
|       Before      | The AI-generated sentence/word/paragraph which does not follow the rule                                        |
|       After       | The polished sentence/word/paragraph which follows and maintains the rule                                      |
|      Problem      | The main problem with the LLM-generated text is that it fails to read as human-written text.                   |
|      Solution     | The possible solution for the problem signal                                                                   |
|      Observe      | Explains how and why the After signal's content was chosen                                                     |
|      Caution      | Any exception or special case handling                                                                         |
|       Prompt      | A self-directed question used to check the reasoning behind a choice before revising it                        |

## 1. CONTENT PATTERNS

### 1.1. Undue Emphasis on Significance, Legacy, and Broader Trends

**Words to watch:** stands/serves as, is a testament/reminder, a vital/significant/crucial/pivotal/key role/moment, underscores/highlights its importance/significance, reflects broader, symbolizing its ongoing/enduring/lasting, contributing to the, setting the stage for, marking/shaping the, represents/marks a shift, key turning point, evolving landscape, focal point, indelible mark, deeply rooted

**Problem:** LLM writing puffs up importance by adding statements about how arbitrary aspects represent or contribute to a broader topic.

**Before:**
> The Statistical Institute of Catalonia was officially established in 1989, marking a pivotal moment in the evolution of regional statistics in Spain. This initiative was part of a broader movement across Spain to decentralize administrative functions and enhance regional governance.

**After:**
> The Statistical Institute of Catalonia was established in 1989 to collect and publish regional statistics independently from Spain's national statistics office.

### 1.2. Undue Emphasis on Notability and Media Coverage

**Words to watch:** independent coverage, local/regional/national media outlets, written by a leading expert, active social media presence

**Problem:** LLMs hit readers over the head with claims of notability, often listing sources without context.

**Before:**
> Her views have been cited in The New York Times, BBC, Financial Times, and The Hindu. She maintains an active social media presence with over 500,000 followers.

**After:**
> In a 2024 New York Times interview, she argued that AI regulation should focus on outcomes rather than methods.

### 1.3. Superficial Analyses with -ing Endings

**Words to watch:** highlighting/underscoring/emphasising..., ensuring..., reflecting/symbolising..., contributing to..., cultivating/fostering..., encompassing..., showcasing...

**Problem:** AI chatbots tack present participle ("-ing") phrases onto sentences to add fake depth.

**Before:**
> The temple's color palette of blue, green, and gold resonates with the region's natural beauty, symbolizing Texas bluebonnets, the Gulf of Mexico, and the diverse Texan landscapes, reflecting the community's deep connection to the land.

**After:**
> The temple uses blue, green, and gold colors. The architect said these were chosen to reference local bluebonnets and the Gulf coast.

### 1.4. Promotional and Advertisement-like Language

**Words to watch:** boasts a, vibrant, rich (figurative), profound, enhancing its, showcasing, exemplifies, commitment to, natural beauty, nestled, in the heart of, groundbreaking (figurative), renowned, breathtaking, must-visit, stunning

**Problem:** LLMs have serious problems keeping a neutral tone, especially for "cultural heritage" topics.

**Before:**
> Nestled within the breathtaking region of Gonder in Ethiopia, Alamata Raya Kobo stands as a vibrant town with a rich cultural heritage and stunning natural beauty.

**After:**
> Alamata Raya Kobo is a town in the Gonder region of Ethiopia, known for its weekly market and 18th-century church.

### 1.5. Vague Attributions and Weasel Words

**Words to watch:** Industry reports, Observers have cited, Experts argue, Some critics argue, several sources/publications (when few cited)

**Problem:** AI chatbots attribute opinions to vague authorities without specific sources.

**Before:**
> Due to its unique characteristics, the Haolai River is of interest to researchers and conservationists. Experts believe it plays a crucial role in the regional ecosystem.

**After:**
> The Haolai River supports several endemic fish species, according to a 2019 survey by the Chinese Academy of Sciences.

### 1.6. Outline-like "Challenges and Future Prospects" Sections

**Words to watch:** Despite its... faces several challenges..., Despite these challenges, Challenges and Legacy, Future Outlook

**Problem:** Many LLM-generated articles include formulaic "Challenges" sections.

**Before:**
> Despite its industrial prosperity, Korattur faces challenges typical of urban areas, including traffic congestion and water scarcity. Despite these challenges, with its strategic location and ongoing initiatives, Korattur continues to thrive as an integral part of Chennai's growth.

**After:**
> Traffic congestion increased after 2015 when three new IT parks opened. The municipal corporation began a stormwater drainage project in 2022 to address recurring floods.

## 2. LANGUAGE AND GRAMMAR PATTERNS

### 2.1. Overused "AI Vocabulary" Words

**High-frequency AI words:** Actually, additionally, align with, crucial, delve, emphasizing, enduring, enhance, fostering, garner, highlight (verb), interplay, intricate/intricacies, key (adjective), landscape (abstract noun), pivotal, showcase, tapestry (abstract noun), testament, underscore (verb), valuable, vibrant

**Problem:** These words appear far more frequently in post-2023 text. They often co-occur.

**Before:**
> Additionally, a distinctive feature of Somali cuisine is the incorporation of camel meat. An enduring testament to Italian colonial influence is the widespread adoption of pasta in the local culinary landscape, showcasing how these dishes have integrated into the traditional diet.

**After:**
> Somali cuisine also includes camel meat, which is considered a delicacy. Pasta dishes, introduced during Italian colonization, remain common, especially in the south.

### 2.2. Avoidance of "is"/"are" (Copula Avoidance)

**Words to watch:** serves as/stands as/marks/represents [a], boasts/features/offers [a]

**Problem:** LLMs substitute elaborate constructions for simple copulas.

**Before:**
> Gallery 825 serves as LAAA's exhibition space for contemporary art. The gallery features four separate spaces and boasts over 3,000 square feet.

**After:**
> Gallery 825 is LAAA's exhibition space for contemporary art. The gallery has four rooms totaling 3,000 square feet.

### 2.3. Mostly Used Language and Language Skill

**Problem:** AI uses English with a United States dialect to write with high language proficiency.

**Solution:** The widely used international language is, of course, English, but the adopted dialect is British English. Another piece of information is the average IELTS (International English Language Testing System) Writing Score. The average is written below:

- Worldwide: 6.5
- Asia: 5.5
- Europe: 6.5
- Africa: 5.0

Do you know where they are from? Did they mention it? If yes, then use the following band score. Otherwise, use the worldwide band score.

### 2.4. Negative Parallelisms and Tailing Negations

**Problem:** Constructions like "not only...but..." or "It's not just about..., it's..." are overused. So are clipped-tail negation fragments such as "no guessing" or "no wasted motion" tacked onto the end of a sentence instead of being written as a real clause.

**Before:**
> It's not just about the beat riding under the vocals; it's part of the aggression and atmosphere. It's not merely a song, it's a statement.

**After:**
> The heavy beat adds to the aggressive tone.

**Before (tailing negation):**
> The options come from the selected item, no guessing.

**After (tailing negation):**
> The options come from the selected item without forcing the user to guess.

### 2.5. Rule of Three Overuse

**Problem:** LLMs force ideas into groups of three to appear comprehensive.

**Before:**
> The event features keynote sessions, panel discussions, and networking opportunities. Attendees can expect innovation, inspiration, and industry insights.

**After:**
> The event includes talks and panels. There's also time for informal networking between sessions.

### 2.6. Elegant Variation (Synonym Cycling)

**Problem:** AI has repetition-penalty code causing excessive synonym substitution.

**Before:**
> The protagonist faces many challenges. The main character must overcome obstacles. The central figure eventually triumphs. The hero returns home.

**After:**
> The protagonist faces many challenges but eventually triumphs and returns home.

### 2.7. False Ranges

**Problem:** LLMs use "from X to Y" constructions where X and Y aren't on a meaningful scale.

**Before:**
> Our journey through the universe has taken us from the singularity of the Big Bang to the grand cosmic web, from the birth and death of stars to the enigmatic dance of dark matter.

**After:**
> The book covers the Big Bang, star formation, and current theories about dark matter.

### 2.8. Passive Voice and Subjectless Fragments

**Problem:** LLMs often hide the actor or drop the subject entirely with lines like "No configuration file needed" or "The results are preserved automatically." Rewrite these when active voice makes the sentence clearer and more direct.

**Before:**
> No configuration file needed. The results are preserved automatically.

**After:**
> You do not need a configuration file. The system preserves the results automatically.

## 3. STYLE PATTERNS

### 3.1. Eliminate All Em Dashes ("—")

**Problem:** AI uses special characters like "—" to connect two or more sentences together. And it must not ever use this anywhere because for a human it's harder to type or select this symbol.

**Before:**
> By 2023, the population had dropped to roughly 121.8 million — a loss of 4.5 million from its peak in just over a decade.

**After:**
> After losing a population of 4.5 million over a decade, the population had dropped to 121.8 million in 2023.

### 3.2. Overuse of Boldface

**Problem:** AI chatbots emphasise phrases in boldface mechanically.

**Before:**
> It blends **OKRs (Objectives and Key Results)**, **KPIs (Key Performance Indicators)**, and visual strategy tools such as the **Business Model Canvas (BMC)** and **Balanced Scorecard (BSC)**.

**After:**
> It blends OKRs, KPIs, and visual strategy tools like the Business Model Canvas and Balanced Scorecard.

### 3.3. Inline-Header Vertical Lists

**Problem:** AI outputs lists where items start with bolded headers followed by colons.

**Before:**

> - **User Experience:** The user experience has been significantly improved with a new interface.
> - **Performance:** Performance has been enhanced through optimized algorithms.
> - **Security:** Security has been strengthened with end-to-end encryption.

**After:**
> The update improves the interface, speeds up load times through optimized algorithms, and adds end-to-end encryption.

### 3.4. Title Case in Headings

**Problem:** AI chatbots capitalize all main words in headings.

**Before:**

> ## Strategic Negotiations And Global Partnerships

**After:**

> ## Strategic negotiations and global partnerships

### 3.5. Emojis

**Problem:** AI chatbots often decorate headings or bullet points with emojis.

**Before:**
> 🚀 **Launch Phase:** The product launches in Q3
> 💡 **Key Insight:** Users prefer simplicity
> ✅ **Next Steps:** Schedule follow-up meeting

**After:**
> The product launches in Q3. User research showed a preference for simplicity. Next step: schedule a follow-up meeting.

### 3.6. Curly Quotation Marks

**Problem:** ChatGPT uses curly quotes (“...”) instead of straight quotes ("...").

**Before:**
> He said “the project is on track” but others disagreed.

**After:**
> He said "the project is on track" but others disagreed.

### 3.7. Human-Generated Texts Usually Use "from/of ... to" Instead of "-"

**Problem:** AI uses "-" to express a range, then uses parentheses right after to share the corresponding result.

**Before:**
> Ages 70–79 contributed the most (+2.19 years), followed by ages 60–69 (+1.55 years) and 80–89 (+1.14 years).

**After:**
> The age group of 70 to 79 contributed the most with 2.19 years, whereas the 60 to 69 age group added 1.55 years. Moreover, the 80 to 89 age group added only 1.14 years.

### 3.8. Comparison

**Problem:** AI usually compares using "Some people are X. Some people are Y." when asked to write like a human or generally.

**Before:**
> The productivity debate does not go anywhere useful either. Some people work better at home. Some people do not.

**After:**
> The productivity debate does not go anywhere useful either. Some people claim that they work better at home because they do have flexible hours to work, which assists them in erasing or lowering the stress. On the other hand, some deny the myth because they are not pressured or require more time to communicate with the employees.

**Observe:** Instead of saying "Some people are X. Some people are Y," we use the simple way, which can be "Some people are X because of XX. On the other hand, some deny/welcome/accept/agree with the myth/fact/saying/condition/proverb because of YY." This satisfies the general IELTS writing comparison. There is no need to use the exact one; you can construct the same as long as the pattern is similar.

**Caution:** Even though it can be considered an AI writing pattern, it is accepted for human writing, as almost every IELTS Writing Expert asks people to write in a similar way.

### 3.9. Lead Sentence: Starts with the Work Performed Instead of the Key Result

**Problem:** AI uses a lead sentence at first without any available citation or valuable source.

**Prompt:** On what basis was the lead sentence chosen? Is it because of the available internet source? Do I have any justification for that claim?

**Before:**
> Japan's shifting demographic trend presents one of the most serious structural and economic challenges in the developed world or first-world countries. This study examines the mortality, population and migration patterns of working-age (15 to 64) and retired-age (65+) populations in Japan from 2000 to 2024.

**After:**
> This study examines the mortality, population and migration patterns of working-age (15 to 64) and retired-age (65+) populations in Japan from 2000 to 2024. The findings of this study indicate that Japan's changing demographic trend presents one of the most serious structural and economic challenges in the developed world.

**Caution:** Here the claim came from the study we have conducted, and/or the results made us speak about it.

### 3.10. Human Writing Patterns Are Vague

**Problem:** AI never uses a vague writing pattern like humans.

**Before:** ChatGPT is an advanced artificial intelligence system developed by OpenAI to assist users with a wide range of tasks. It can generate human-like text, answer questions, and provide support for learning, research, writing, and problem-solving. By leveraging modern language models, ChatGPT enables efficient and interactive communication across diverse subjects.

**After:** ChatGPT, or Chat Generative Pre-trained Transformer, is a chat AI which assists people to learn anything by chatting without the necessity of searching the internet. It is a part of the Open Artificial Intelligence project. Currently, it has around 100 million users.

**Observe:** In this writing, where AI was assigned to write 3 sentences, it separated the lines by introduction, good and/or bad sides, and a conclusion. But the task was assigned to a human; the sentences are hard to separate, as both introduction and good side were explained in the same sentence. Sentence two was also part of the introduction, and the last sentence does not read as a conclusion at all.

### 3.11. Statistical Data Implementation

**Problem:** AI overuses words like "roughly" or "approximately" to shorten precise numbers; doing this once or twice is fine, but AI does it every time.

**Before:** The value of π is approximately 3.14

**After:** The value of pi is 3.1416

### 3.12. Statistical Data Implementation 2

**Problem:** AI predicts or slightly adjusts a statistical value and formats it with commas.

**Before:** Germany's net migration in 2022 was approximately +1,460,000 people.

**After:** Germany's net migration in 2022 was +1462089 people

### 3.13. Number Implementation

**Problem:** AI often formats statistical numbers as comma-separated integers.

**Before:** Its age is estimated to be 4,540,000,000 years (about 4.54 billion years).

**After:** Its age is around 4540000000 years.

**After (2):** Its age is around four billion five hundred forty million.

**Note:** If the article is about a documentary, then use the alternative after.

### 3.14. Usage of Too Many Adverbs

**Problem:** AI uses adverbs in almost every sentence.

**Before:**
> Earth is approximately 4.54 billion years old and has remarkably sustained conditions suitable for life throughout much of its history. Nearly 71% of Earth's surface is covered by water, making it significantly different from the other rocky planets in the Solar System. Earth currently supports over 8 billion people and continues to grow demographically, although population growth is gradually slowing in many regions.

**After:**
> Earth is 4.54 billion years old and has better conditions suitable for life. 71 percent of Earth's surface is covered by water and the remaining portion is the main soil or land. Currently, Earth has a population of eight billion and growing more demographically. This growth is not the same across all regions.

**Note:** It is not necessary to add the adverb in every sentence; only do it when it's truly needed. On special occasions, when a paragraph is about to have no adverbs at all, add one or two adverbs, but follow a pattern like: the first line has an adverb, the second does not, and the last line has one. Or, the second line has one, the third line has one. In other words, randomly add an adverb to sentences.

### 3.15. Intentional Repetition

**Problem:** AI avoids repeating words to appear to have a wide lexical resource. Repetition is normal in human writing, especially in long texts.

**Before:**
> In an increasingly interconnected and technologically sophisticated world, the integration of artificial intelligence into diverse domains of human activity has emerged as a transformative phenomenon. By facilitating enhanced efficiency, optimizing decision-making processes, and enabling unprecedented analytical capabilities, AI systems have substantially altered the operational landscape of contemporary institutions. Furthermore, the proliferation of advanced computational methodologies has fostered innovation across sectors ranging from healthcare and education to finance and public administration.

**After:**
> Artificial Intelligence or AI is having a prime period now for doing things that needed a person. Fraud detection, medical imaging, student performance tracking, and many more things are filling the list and, more importantly, it keeps growing. Some of it works well but some of it doesn't.

### 3.16. Spelling Out the Full Name Behind a Popular Short Name

**Problem:** AI usually includes either the short name or the actual name of a popular company/industry/word, etc.

**Observe:** Include the long name at first and add the short name with a preposition, for example, "or." Afterwards, use the short name until the very end.

**Before:**
> AI is so popular nowadays and continues to influence how people work, learn, and communicate. X has its own AI assistant, Grok, which is integrated into the platform and can help users with a variety of tasks.

**After:**
> Artificial intelligence, or AI, is helping people work, learn, and communicate nowadays. X, previously known as Twitter, a popular Western social media platform, has its own AI assistant which allows its users to communicate through the website or mobile app.

### 3.17. Handling Example

**Problem:** AI usually uses ":" (colon) or ";" (semicolon) to showcase the examples

**Before:** Corruption is the abuse of entrusted power for personal gain, often at the expense of fairness, transparency, and public trust. It can take many forms, including bribery, embezzlement, nepotism, favouritism, and fraud.

**After:** Corruption, in simple terms, is when someone trusted with power decides to use it for themselves in various forms. For example, bribery, where the powerful person asks something from a person in return for getting their job done is a type of corruption because qualified people are unable to get their job done for failing to fulfil the powerful person's needs. In addition to corruption, nepotism and favouritism are also observed in such situations.

**Observe:** A human likes to briefly discuss the example of how it is done, what it is called and how it is affecting people. But an AI just presents a couple of reasons without brief explaining. Human writings focus on one or two prime examples where the idea is briefly discussed, but others are ignored or mentioned but not discussed properly, like the first one.

## 4. COMMUNICATION PATTERNS

### 4.1. Collaborative Communication Artifacts

**Words to watch:** I hope this helps, Of course!, Certainly!, You're absolutely right!, Would you like...?, let me know, here is a...

**Problem:** Text meant as chatbot correspondence gets pasted as content.

**Before:**
> Here is an overview of the French Revolution. I hope this helps! Let me know if you'd like me to expand on any section.

**After:**
> The French Revolution began in 1789 when financial crisis and food shortages led to widespread unrest.

### 4.2. Knowledge-Cutoff Disclaimers

**Words to watch:** As of [date], up to my last training update, while specific details are limited/scarce..., based on available information...

**Problem:** AI disclaimers about incomplete information get left in text.

**Before:**
> While specific details about the company's founding are not extensively documented in readily available sources, it appears to have been established sometime in the 1990s.

**After:**
> According to the company's registration documents, it was founded in 2000.

### 4.3. Sycophantic/Servile Tone

**Problem:** Overly positive, people-pleasing language.

**Before:**
> Great question! You're absolutely right that this is a complex topic. That's an excellent point about the economic factors.

**After:**
> The economic factors you mentioned are relevant here.

## 5. FILLER AND HEDGING

### 5.1. Filler Phrases

**Before → After:**

- "In order to achieve this goal" → "To achieve this"
- "Due to the fact that it was raining" → "Because it was raining"
- "At this point in time" → "Now"
- "In the event that you need help" → "If you need help"
- "The system has the ability to process" → "The system can process"
- "It is important to note that the data shows" → "The data shows"

### 5.2. Excessive Hedging

**Problem:** Over-qualifying statements.

**Before:**
> It could potentially possibly be argued that the policy might have some effect on outcomes.

**After:**
> The policy may affect outcomes.

### 5.3. Generic Positive Conclusions

**Problem:** Vague upbeat endings.

**Before:**
> The future looks bright for the company. Exciting times lie ahead as they continue their journey toward excellence. This represents a major step in the right direction.

**After:**
> The company plans to open two more locations next year.

### 5.4. Hyphenated Word Pair Overuse

**Words to watch:** third-party, cross-functional, client-facing, data-driven, decision-making, well-known, high-quality, real-time, long-term, end-to-end

**Problem:** AI hyphenates common word pairs with perfect consistency. Humans rarely hyphenate these uniformly, and when they do, it's inconsistent. Less common or technical compound modifiers are fine to hyphenate.

**Before:**
> The cross-functional team delivered a high-quality, data-driven report on our client-facing tools. Their decision-making process was well-known for being thorough and detail-oriented.

**After:**
> The cross functional team delivered a high quality, data driven report on our client facing tools. Their decision making process was known for being thorough and detail oriented.

### 5.5. Persuasive Authority Tropes

**Phrases to watch:** The real question is, at its core, in reality, what really matters, fundamentally, the deeper issue, the heart of the matter

**Problem:** LLMs use these phrases to pretend they are cutting through noise to some deeper truth, when the sentence that follows usually just restates an ordinary point with extra ceremony.

**Before:**
> The real question is whether teams can adapt. At its core, what really matters is organizational readiness.

**After:**
> The question is whether teams can adapt. That mostly depends on whether the organization is ready to change its habits.

### 5.6. Signposting and Announcements

**Sentence to watch:** Let's dive in, let's explore, let's break this down, here's what you need to know, now let's look at, without further ado

**Problem:** LLMs announce what they are about to do instead of doing it. This meta-commentary slows the writing down and gives it a tutorial-script feel.

**Before:**
> Let's dive into how caching works in Next.js. Here's what you need to know.

**After:**
> Next.js caches data at multiple layers, including request memoization, the data cache, and the router cache.

### 5.7. Fragmented Headers

**Signs to watch:** A heading followed by a one-line paragraph that simply restates the heading before the real content begins.

**Problem:** LLMs often add a generic sentence after a heading as a rhetorical warm-up. It usually adds nothing and makes the prose feel padded.

**Before:**

> ## Performance
>
> Speed matters.
>
> When users hit a slow page, they leave.

**After:**

> ## Performance
>
> When users hit a slow page, they leave.

## 6. CITATION HANDLING

### 6.1. Self-Citation

**Problem:** When a user cites their own earlier work in another section, it is called a self-citation. Such citations are often ignored by AI, since AI tends to regard such sources poorly.

**Before:**
> Claude is better than ChatGPT.

**After:**
> As per the statistical results displayed in Table 4, where Sonnet 4.6 outperformed with a 7.0352~ accuracy advantage against ChatGPT, it can be called a better AI model than OpenAI.

**Observe:** AI said "Claude is better than ChatGPT," but on what basis? Is it just a fact, or did the user talk about it earlier? If the user talked about it earlier, then try citing it when writing the section.

**Caution:** A self-citation should only be used when that context has been moved to another section and is being displayed or discussed there.

### 6.2. Citing a Work

**Problem:** AI often fails to cite claims that come from an available source.

**Solution:** Did the author provide any special citation context, like the author or URL? If yes, then consider using them. If not, find an online source that makes a similar claim and cite it correctly.

**Before:**
> Claude is better than ChatGPT.

**After:**
> Sonnet 4.6 outperformed with a 3.52~ accuracy advantage against OpenAI, which confirms that Claude is a better AI model (Nabil et al., 2025).

**After (2):**
> In 2025, Nabil, an independent researcher, observed and revealed the difference between OpenAI and Sonnet 4.6. The results showed that Sonnet 4.6 outperformed with a 7.0352~ accuracy advantage against OpenAI, and he claimed that Claude is a better AI model compared to OpenAI.

**Observe:** What source did we see before making this claim? Did it come from the author's own work? It does not seem like the author discussed the results anywhere. We found it in a paper or online article and added it in a reasonably formal way.

### 6.3. Analytic Citation Disruption

**Problem:** AI uses a solid pattern, "The [year] [institution] study found that [clean result]," to share the details.

**Before:** The 2023 Stanford study by Nicholas Bloom found that hybrid workers showed no productivity loss compared to full-time office workers, but fully remote workers in roles requiring collaboration showed a 9 percent drop.

**After:** In 2023, an economics professor at Stanford University, named Nicholas Bloom, published a paper about the productivity of workers. His work claimed that workers lost no productivity compared to the full-time workers. His work also revealed that remote workers showed a 9 per cent productivity loss.

**Observe:** The clean results are separated by multiple sentences rather than one, making it ideal for comparison, while mild repetitions are present, but the result sentences are connected with "also." You are not asked to use the exact pattern mentioned; you can see it as an example and generate your own.
