# Formal Writing Guidance

---

This guidance is only applicable if

- user asked to use formal pattern for writing
- user asked to generate technical report/report/research paper/formal writing content
- user's meant to use it to replace the existing section/paraphrah of their formal paper/work. They will usually mention "I wish to replace the parapraph with my existing formal work/paper"

otherwise ignore the file. A conversational file does not require any of these rules to follow except asked by user.

**Example Input (When the file should be triggered or worked):**
> Can you assist me making a formal paper. The topic is [TOPIC].
> Can you correct the citation of the [file]?
> Rewrite this text in formal way.
> Here is the paper of mine, use it as a reference for my formal writing. And continue writing about [TOPIC]

---

## 1. CITATION (Optional, if asked by user to fix citation for the text, pass otherwise)

### 1.1. Self-Citation

**Problem:** When a user cites their own earlier work in another section, it is called a self-citation. Such citations are often ignored by AI, since AI tends to regard such sources poorly.

**Before:**
> Claude is better than ChatGPT.

**After:**
> As per the statistical results displayed in Table 4, where Sonnet 4.6 outperformed with a 7.0352~ accuracy advantage against ChatGPT, it can be called a better AI model than OpenAI.

**Observe:** AI said "Claude is better than ChatGPT," but on what basis? Is it just a fact, or did the user talk about it earlier? If the user talked about it earlier, then try citing it by mentioning where they have proved their claim.

**Caution:** A self-citation should only be used when that context has been moved to another section and is being displayed or discussed there.

### 1.2. Citing a Work

**Problem:** AI often fails to cite claims that come from an available source.

**Solution:** Did the author provide any special citation context, like the author or URL? If yes, then consider using them. If not, find an online source that makes a similar claim and cite it correctly.

**Before:**
> Claude is better than ChatGPT.

**After:**
> Sonnet 4.6 outperformed with a 3.52~ accuracy advantage against OpenAI, which confirms that Claude is a better AI model (Nabil et al., 2025).

**After (2):**
> In 2025, Nabil, an independent researcher, observed and revealed the difference between OpenAI and Sonnet 4.6. The results showed that Sonnet 4.6 outperformed with a 7.0352~ accuracy advantage against OpenAI, and he claimed that Claude is a better AI model compared to OpenAI.

**Observe:** What source did we see before making this claim? Did it come from the author's own work? It does not seem like the author discussed the results anywhere. We found it in a paper or online article and added it in a reasonably formal way.

### 1.3. Analytic Citation Disruption

**Problem:** AI uses a solid pattern, "The [year] [institution] study found that [clean result]," to share the details.

**Before:** The 2023 Stanford study by Nicholas Bloom found that hybrid workers showed no productivity loss compared to full-time office workers, but fully remote workers in roles requiring collaboration showed a 9 percent drop.

**After:** In 2023, an economics professor at Stanford University, named Nicholas Bloom, published a paper about the productivity of workers. His work claimed that workers lost no productivity compared to the full-time workers. His work also revealed that remote workers showed a 9 per cent productivity loss.

**Observe:** The clean results are separated by multiple sentences rather than one, making it ideal for comparison, while mild repetitions are present, but the result sentences are connected with "also." You are not asked to use the exact pattern mentioned; you can see it as an example and generate your own.

### 1.4. Citation for Facts or Known texts

**Problem:** A citation of a fact is not needed but AI still tries to cite it.

**Before:**
> According to wikipedia, Earth is 4.5 billion years old.

**After:**
> Earth is 4.5 billion years old.

**Observe:** The age of earth is a common sense and pretty much every human knowns it. Thus, citing this sentence is not needed.

## 2. Finding the Paper type (Optional, if asked by user to send/generate a file, pass otherwise)

An important task for AI is to find what citation style, template, structure and output format fits for the topic.

The table confirms which style should be used for the selected topic.

| Domain                  | Common Citation Styles | Common Structure       | Preferred Template    | Typical Output |
| :---------------------: | ---------------------- | ---------------------- | --------------------- | -------------- |
| Computer Science        | IEEE, ACM              | IMRAD                  | IEEE/ACM              | LaTeX, PDF     |
| Software Engineering    | IEEE, ACM              | IMRAD                  | IEEE                  | LaTeX, DOCX    |
| Artificial Intelligence | IEEE, ACM, Nature      | IMRAD                  | NeurIPS, ICML, IEEE   | LaTeX, PDF     |
| Data Science            | APA, IEEE              | IMRAD                  | IEEE, Springer        | LaTeX, DOCX    |
| Cybersecurity           | IEEE, ACM              | IMRAD                  | IEEE                  | LaTeX, PDF     |
| Electrical Engineering  | IEEE                   | IMRAD                  | IEEE                  | LaTeX, PDF     |
| Mechanical Engineering  | IEEE, ASME             | IMRAD                  | ASME                  | LaTeX, PDF     |
| Civil Engineering       | ASCE, IEEE             | IMRAD                  | ASCE                  | PDF, DOCX      |
| Mathematics             | AMS                    | Theorem-Based          | AMS                   | LaTeX, PDF     |
| Physics                 | APS, AIP               | IMRAD                  | RevTeX                | LaTeX, PDF     |
| Chemistry               | ACS                    | IMRAD                  | ACS                   | DOCX, PDF      |
| Biology                 | APA, Nature, Cell      | IMRAD                  | Journal-specific      | DOCX, PDF      |
| Medicine                | Vancouver, AMA         | IMRAD                  | ICMJE                 | DOCX, PDF      |
| Nursing                 | APA                    | IMRAD                  | APA                   | DOCX           |
| Psychology              | APA                    | IMRAD                  | APA                   | DOCX, PDF      |
| Sociology               | APA, ASA               | IMRAD or Essay         | ASA                   | DOCX           |
| Economics               | APA, Chicago           | IMRAD or Working Paper | AEA                   | LaTeX, PDF     |
| Business                | APA, Harvard           | IMRAD                  | APA                   | DOCX           |
| Education               | APA                    | IMRAD                  | APA                   | DOCX           |
| Law                     | Bluebook, OSCOLA       | Legal Analysis         | Jurisdiction-specific | DOCX           |
| Philosophy              | MLA, Chicago           | Argumentative Essay    | Chicago/MLA           | DOCX, PDF      |
| History                 | Chicago                | Narrative Analysis     | Chicago               | DOCX           |
| Political Science       | APA, Chicago           | IMRAD                  | APSA                  | DOCX, PDF      |
| Linguistics             | APA, LSA               | IMRAD                  | LSA                   | LaTeX, DOCX    |

If user had specified any topic and/or Title but not domain, find their topic's domain from the domains mentioned in the table. If user had not specific any topic or domain, then you must see this section once you are done making the title of the work. You will provide the text output if requested by user.
