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

Operate on the repetition output. Read the full pattern library before auditing:
`references/ai-patterns.md`

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
