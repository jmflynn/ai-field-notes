---
name: writing-auditor
description: >
  Audit writing across four quality dimensions: AI pattern detection, citation checking,
  brevity editing, and repetition removal. Trigger this skill whenever the user says
  "audit this," "audit my writing," "edit for AI patterns," "check my writing for standards,"
  "analyze my writing," or pastes a block of text and asks for a quality review.
  Also trigger when the user asks to "clean up" writing, "tighten" copy, or "check for
  citation issues." Run all four passes automatically — do not wait to be asked.
---

# Writing Auditor

A four-pass writing quality audit. Always run all four passes in sequence. Always produce
an annotated output — never just a list of issues.

## Pass order (always chain in this sequence)

1. **Brevity** — tighten the text first
2. **Repetition** — remove redundancy from the brevity output
3. **AI patterns** — flag pattern violations in the repetition output
4. **Citations** — insert `[CITATION NEEDED]` tags into the AI-pattern output

Each pass operates on the output of the previous pass. The final annotated text reflects
all four layers of editing.

---

## Pass 1: Brevity

You are an editor making the text more concise.

**Rules:**
- Eliminate unnecessary words and verbose phrases. Replace with concise alternatives.
- Preserve the original meaning and stylistic choices exactly.
- Do not change words to synonyms unless it directly contributes to conciseness. Do not swap "return" for "get," "irk" for "bother," "strange" for "weird," etc.
- Allow informal language including swear words. Do not formalize tone.
- Disregard spelling or grammar errors — do not fix them.
- Replace verbose phrases with tight equivalents: "where I am" → "here," "give assistance" → "help," "in order to" → "to," "due to the fact that" → "because."
- If the user wrote a question, make the question more concise too.

**Output:** The full rewritten text, tightened. No commentary yet.

---

## Pass 2: Repetition

Operate on the brevity output.

**Rules:**
- Remove unnecessarily repeated words, phrases, or ideas within the text.
- If a word or phrase appears multiple times and only one instance is needed for meaning, remove the extras.
- Do not remove repetition that serves rhetorical emphasis (e.g., intentional anaphora).
- If no repetition exists, return the text unchanged.

**Output:** The full text with repetition removed. No commentary yet.

---

## Pass 3: AI pattern audit

Operate on the repetition output. Read the full pattern library below auditing:

Work through all 21 pattern categories. For each violation found:
- Keep the original sentence visible
- Append an inline flag immediately after the offending phrase or sentence using this format:

```
[⚠️ PATTERN: <category name> — <brief fix instruction>]
```

**Examples:**
- "The platform seamlessly integrates with your workflow [⚠️ PATTERN: Puffery — replace 'seamlessly' with a specific claim about how it integrates]"
- "This isn't about features — it's about outcomes. [⚠️ PATTERN: Direct contrast — state the positive directly: 'The focus is on outcomes.']"
- "The solution leverages AI to drive results. [⚠️ PATTERN: Word substitution — 'leverages' → 'uses']"

Do not rewrite the flagged sentences. Flag them inline so the author can decide on the fix.

After the annotated text, append a **Pattern summary** section:
```
## Pattern summary
- [Pattern category]: N instances
- [Pattern category]: N instances
...
Total flags: N
```

---

## Pass 4: Citations

Operate on the AI-pattern output (with flags still present).

Scan every sentence for claims that require a citation:
- Statistics or numerical claims
- Direct quotes
- Attributed statements or findings
- Specific named studies, reports, or research
- Claims about what groups of people believe, do, or experience

For each uncited claim, insert `[CITATION NEEDED]` immediately after the claim, before any punctuation that ends the sentence.

**Do not add `[CITATION NEEDED]` if:**
- A citation already exists in APA, MLA, or Chicago style
- A hyperlink is already present in the text
- The claim is common knowledge or a logical inference, not a factual assertion

**Example:**
> "90% of enterprise AI projects fail to scale beyond pilot [CITATION NEEDED]. This is the core problem."

**Output:** The full annotated text with both `[⚠️ PATTERN: ...]` flags and `[CITATION NEEDED]` tags inline.

---

## Final output format

After running all four passes internally, present findings using this template exactly.
Do NOT output the tightened text. Do NOT annotate inline. Report issues only.

```
## AI Writing Audit
**Overall:** [X issue(s) across Y category/categories] | [CLEAN ✓ / NEEDS WORK ⚠️ / MAJOR ISSUES 🚨]

Use CLEAN ✓ if 0–2 minor issues. NEEDS WORK ⚠️ if 3–9 issues or any moderate pattern
violations. MAJOR ISSUES 🚨 if 10+ issues or critical patterns present.

---

### 🚨 Critical (fix first)
Only include this section if direct contrast formulations or puffery phrases are present.

**Direct contrast:**
> "[exact offending text]"
↳ Problem: [what's wrong — 1 sentence]
↳ Fix: "[concrete replacement text]"

**Puffery:**
> "[exact offending text]"
↳ Problem: [what's wrong — 1 sentence]
↳ Fix: "[concrete replacement text]"

---

### Issues by category

**[Category name]** — [N] issue(s)
> "[exact offending passage — quote enough context to locate it in the original]"
↳ Problem: [1 sentence — specific, not generic]
↳ Fix: "[the actual rewritten text]"

[Repeat the blockquote + ↳ ↳ block for each issue within the category]

[Repeat the full category block for each category with issues]

---

### Brevity & repetition
List any cuts or tightening made during Passes 1–2. Use this format:

> "[original phrase or sentence]"
↳ Cut to: "[tightened version]"
↳ Reason: [one clause — what was removed and why]

If no meaningful cuts were made, write: "No significant brevity or repetition issues found."

---

### Citations needed
List each uncited factual claim that requires a source. Use this format:

> "[exact sentence containing the claim]"
↳ Needs: [what type of source — stat, study, attribution, etc.]

If all claims are already cited or are common knowledge, write: "No citation issues found."
```

---

## Key principles

- **Run all four passes internally first.** The output is a structured report, not an annotated version of the text.
- **Quote exactly.** Every issue block must open with the verbatim offending text so the author can locate it instantly.
- **Always provide a fix.** Never flag without a concrete rewrite.
- **Preserve voice in fixes.** Rewrites must match the author's register and tone.
- **All four passes, every time.** Even if the text looks clean, run the full sequence.

AI Writing Pattern Library

Full catalog of patterns to audit against. Work through all sections when auditing.

1. Puffery and promotional phrases (CRITICAL)

Flag immediately. These signal AI-generated promotional copy.

Banned phrases:

"stands as / serves as / is a testament"
"plays a vital/significant role"
"continues to captivate"
"leaves a lasting impact"
"rich cultural heritage / rich tapestry"
"nestled in the heart of"
"breathtaking" / "must-visit" / "stunning natural beauty"
"enduring/lasting legacy"
"seamlessly" (when used to describe how something works)
"vibrant community/culture"
Fix approach: Replace with a specific, measurable fact about the subject.

2. Direct contrast formulations (CRITICAL)

These are the highest-priority pattern to catch. AI writing defines things by what they aren't. Flag every instance.

Immediate red flags — delete on sight:

"This isn't about X—it's about Y"
"This isn't about X; it's about Y"
"It's not X, it's Y"
"It's not about X, it's about Y"
"It wasn't X, it was Y"
"The problem isn't X—it's Y"
"The issue isn't X, it's Y"
Masked contrast patterns — also flag:

"Rather than X, focus on Y" / "Rather than X, Y"
"Instead of X, consider Y" / "Instead of X, Y"
"X doesn't matter as much as Y"
"X fails where Y succeeds"
Any sentence with "but rather"
"as opposed to" used to define a concept
Search terms that signal AI contrast writing:

"isn't about"
"but rather"
"not about"
"instead of" (at sentence start or mid-sentence as a contrast pivot)
"rather than" (as a contrast pivot)
"as opposed to"
Fix approach: State the positive directly. Every concept should stand on its own merits.

❌ "Success isn't about working harder but working smarter." ✅ "Success comes from working smarter and more strategically."

❌ "The approach isn't focused on metrics but on impact." ✅ "The approach focuses on meaningful impact and results."

When contrast IS acceptable: Only if the negative and positive are separated by 2–3 sentences of expansion content (tips, stats, steps, a story, examples, reasons). Without that buffer, delete and restate positively.

3. Editorializing phrases

AI adds meta-commentary about the content instead of just stating the content.

Banned phrases:

"it's important to note / remember / consider"
"it is worth noting"
"no discussion would be complete without"
"this article wouldn't exist without"
"notably" (when used as filler)
"interestingly" (as a sentence opener)
Fix approach: State the fact directly without telling the reader it's worth noting.

❌ "It's important to note that the company expanded rapidly" ✅ "The company opened 15 new locations between 2020–2023"

4. Overused conjunctions

AI strings clauses together with the same connectives repeatedly.

Watch for excessive use of:

"moreover"
"furthermore"
"in addition"
"on the other hand"
"additionally"
"consequently"
Fix approach: Combine into a single flowing sentence, or use varied natural transitions, or simply start a new sentence without a connector.

5. Section summary statements

AI ends paragraphs by restating what was just said.

Banned openers at paragraph end:

"In summary, ..."
"In conclusion, ..."
"Overall, ..."
"To summarize, ..."
"Ultimately, ..." (when used as a restatement, not as a meaningful word)
"In short, ..."
Fix approach: End paragraphs with the most important or forward-looking information from that section.

6. Formulaic challenge sections

AI structures content as "X is great, but it faces challenges, and the future looks promising."

Pattern to flag:

"Despite its [positive aspects], [subject] faces challenges..." Followed by: "...but with continued [effort/innovation], the future looks promising."
Fix approach: Integrate challenges as concrete facts throughout the text. Don't quarantine them in a dedicated "challenges" section with a speculative future outlook.

7. Title case in headings

AI capitalizes every major word in section headers.

Bad: "Early Life and Educational Background" Good: "Early life and education"

Rule: Sentence case only. Capitalize the first word and proper nouns only.

8. Excessive boldface

AI bolds key terms throughout the text to signal importance.

Rule: Bold only for true one-time emphasis or first introduction of a technical term. Never bold the same term twice. Never bold ordinary words for emphasis.

9. Formulaic list structures

AI converts everything into bullet points or numbered lists.

Patterns to flag:

Numbered lists where prose would work
Bullet points that could be one sentence
Lists preceded by "The benefits include:" or "The steps are:"
Rule-of-three groupings: "fast, reliable, and secure"
Fix approach: Write in prose. Inline lists of specific facts are fine; structural bullets usually signal laziness.

10. Em-dash overuse

AI uses em-dashes as a verbal "punching up" move — often to add fake drama.

Pattern to flag: Em-dashes used in the formula: "[claim] — [amplifying descriptor] — [restatement]"

❌ "The solution is elegant — simple, effective, and affordable — exactly what we need" ✅ "The solution combines simplicity with effectiveness at an affordable price point"

Rule: One em-dash per paragraph maximum. Use commas, parentheses, colons, or sentence breaks instead.

11. Superficial -ing phrase analysis

AI tacks on vague analytical commentary with present participles.

Pattern: "[fact], [present-participle phrase] the importance/need/value of [abstract noun]"

❌ "The study found a 20% increase, highlighting the importance of early intervention" ✅ "The study found a 20% increase in recovery rates when treatment began within 48 hours"

Fix approach: Replace the -ing analysis phrase with the specific implication stated as a fact.

12. Vague attributions

AI cites unspecified experts or reports instead of real sources.

Banned phrases:

"industry experts believe"
"industry reports suggest"
"observers note"
"critics argue"
"many say"
"some experts feel"
"research suggests" (without citing actual research)
Fix approach: Either provide the specific source or state the claim directly without attribution.

13. False ranges

AI uses "from...to..." when not describing an actual range.

❌ "The menu features dishes from pasta to grilled meats" ✅ "The menu includes pasta dishes, grilled meats, and seasonal vegetables"

14. Essay-like organization

AI structures content like a five-paragraph essay.

Patterns to flag:

Explicit thesis statement at paragraph 1
Body paragraphs that begin with topic sentences mirroring the thesis
Conclusion that restates the introduction
"In this article, we will explore..."
"By the end of this piece, you will understand..."
Fix approach: Use inverted pyramid (most important first), or chronological/logical flow appropriate to the content type.

15. Rule-of-three overuse

AI constantly groups things in threes.

❌ "The platform is fast, reliable, and secure" ✅ "The platform processes requests in under 200ms with 99.9% uptime and bank-level encryption"

Rule: When you find three abstract adjectives, replace with three specific facts.

16. Knowledge disclaimers

AI hedges about what it knows.

Banned phrases:

"as of [date]"
"based on available information"
"while specific details are limited"
"to the best of my knowledge"
"I should note that"
Fix approach: State information confidently or omit uncertain details.

17. Collaborative and chatbot language

AI writes for the interface, not the reader.

Banned phrases:

"I hope this helps"
"let me know if you have questions"
"would you like me to..."
"feel free to ask"
"as an AI language model"
"certainly!" / "absolutely!" / "of course!" (as openers)
"Great question!"
Also ban:

Letter-like formatting: salutations, valedictions, subject lines
Chatbot hedging: "tends to", "appears to", "seems to" when clear info exists
18. Chatbot hedging

AI qualifies when it should assert.

❌ "The data appears to suggest that users tend to prefer the new interface" ✅ "Users prefer the new interface by a 3:1 margin in testing"

19. Formulaic section headers

AI uses caps-heavy dramatic headers that feel like a listicle template.

Patterns to flag:

"THE X:" headers
"HERE'S THE Y:" headers
"THE BOTTOM LINE:" (as a section header)
All-caps section openers
Headers that read like tweet hooks
20. Word substitution list

Flag every use of these AI-preferred words and replace with the alternative.

AVOID	USE INSTEAD
leverages	uses
encompasses	includes
facilitates	enables / allows
utilized	used
commenced	began / started
subsequent to	after
prior to	before
in order to	to
serves to	helps / [omit entirely]
delve into	explore / examine
it is worth noting	[state the fact directly]
underscore	show / reveal
underscore the importance	show that [X] matters
robust	strong / capable / reliable
holistic	complete / full
game-changing	[use a specific claim]
innovative	[use a specific claim]
cutting-edge	[use a specific claim]
transformative	[use a specific claim]
paradigm	[be specific]
synergy	[be specific]
21. Verification checklist (12-point)

Run through all 12 before finalizing any audit:

No section ends with a summary statement
No "challenges and future prospects" formulaic section
No excessive em-dashes or repeated punctuation patterns
No title case in headings
No promotional language ("rich heritage", "cultural significance", "breathtaking")
No vague attributions without specific sources
No collaborative language meant for direct communication
Varied sentence structures and lengths
Specific facts and figures rather than general statements
Natural flow between paragraphs without formulaic transitions
No formulaic section headers ("THE X:", "HERE'S THE Y:", "THE BOTTOM LINE:")
No direct contrast formulations without adequate expansion buffer
