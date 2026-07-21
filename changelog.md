# CHANGELOG

## 0.3.0 (22nd July, 2026)

- This is the end of "Become-Human" era. All services are now available as "BeHuman", a short name to memorise and write.
- We have noticed and observed that PSPM itself is costing a lot of tokens for Claude. We found the root cause of this incident is unwanted files that the AI should not read such as readme(~1,947), WARP (~599), changelog (~844) and credits(~500). We have implemented a small patch on the SKILL.md for AI to completely avoid this running until requested by user. New version is expected to reduce the token draining by 33%.
- We noticed some complains regarding the poor quality of writing. At first let us make it clear, behuman is intended to completely fake your personality, writing habit, and quality. If you are providing a sample that is poorly writen, the skill just adopts that quality automatically. We have implemented a fix and the system should provide the maximum quality if a sample is not provided. An additional thing is, the skill will no longer force you with dropdown questions anymore (hopefully).
- Lexical Surprise is reworked. Couple of examples were added after noticing the previous version was breaking the idioms/phrases with lexical surprise. Previous version was not even seeing that how awkward a word can be when selected the 2nd and/or 3rd best word which is fixed in this version with examples. We have moved from registered-common words to ofxord 5000 word list for common words pattern. The file is shared as well, if you see any common words but not listed in oxford 5000, consider adding them. If you locally preserve the file, the output can be as sweet as butter (speaking of butter, it already made me hungry).
- Some patterns are moved to `writing-thinking` dir and/or reworked.
- Solution for each problem is added. You may see some contents may contain the solution section yet but they will be added in the future version.
- We wish to say goodbye to the pattern replacement, for example, change X with Y. But we wish to implement an independent way (for the AI to resolve the issue by itself cause AI is not longer dumb) to keep up with both formal writing and conversational writing.
- `reference.md` was renamed with `credits.md` because some Agentic AI was automatically detecting the file as honey for them to gain. Too bad, they were fooled up until now.
- `./ext/words.csv` is added which lists all words of oxford 5000.
- Added `SECURITY.md`.
- Updated support for Sonnet 5, OpenAI 5.6, Kimi K3, Qwen 3.6 and any before versions.
- `WARP.md` is reworked. Specially where agents were confused regarding how the process should be done and which file to skip or use.
- **Citation** and **Formatting** for formal writing is introduced but not patched fully.
- Upcoming versions will deeply focus on writing variants until some new issues pops up.

## 0.2.2

- Added `WARP.md` for AI Agents
- Introduced `pre-pass.md` which checks the personality and habits before writing
- Introduced `post-pass.md` which handles the human behaviour after the content is fully written inside the memory.
- Renamed `pspm.md` with PSPM.md as its a major file.
- Expended the contents of both pre-pass and post-pass which real life example and cases.
- `SKILL.md` was reworked to avoid repeated content after spliting contents to pre-pass and post-pass. Process of SKILL.md was not working the way how it should be which is fixed in this version
- Moved Citation from `pattern.md` to `./writing-thinking/formal.md` because our observation noticed conversational mode does not require ciation. Citation feature can still be used if asked by user.

## 0.2.1

- published the public version
- updated the readme with informations

## 0.2.0

- Introduced some more patterns.
- Reworked the evidence.md file completely.

## 0.1.9

- pattern.md is introduced which handles and indicates the common and most used AI-writing pattern. (Just a fork version of humanizer without some minor polish, but planned to be updated later)
- introduced `./writing-thinking/` dir which handles the special instructions for writing and thinking styles like conversational, formal, in between, native, non-native etc.
- evidence file now contains special instructions for the pspm calculation and avoids the hot-loop of running.
- splited the pspm section from skill.md to pspm.md so improve the visibility.

## 0.1.8

- Introduced the external evidence for justification made by PSPM. Earlier version was fully AI dependent causing a hot loop and confusion for AI.
- Reworked the self-citation section completely to handle both external and internal citations.
- Removed additional white-spaces.

## 0.1.7

- Added Lexical Surprise Section
- Added citation-wise writing
- Added global IELTS writing score
- Added some regional IELTS writing score
- Introduced Writing Tone or proficiency problems
- Fixed an issue where pspm calculation was running without any accepted uncertainty rate
- Fixed some typos and spelling mistakes.
- PSPM confidence has been introduced.
- Fixed the task order which was hindering some sections from running

## 0.1.6

- Introduced PSPM to calculate if it sounds human statistically
- Become Human can now also detect AI texts.

## 0.1.5

- Available for public distribution. Nyehehehehheh~

## 0.1.4 - 0.1.0

- For god's sake, please trust us that we forgot what changes were made because of our other work!!! Meeeoww!
