---
name: tutorial-generator
description: Generate structured AI workflow and tool tutorials in a consistent format, then push them directly to Notion. Trigger this skill whenever the user asks to "create a tutorial," "write a tutorial," "document a workflow," "make a step-by-step guide," or describes a process they want captured as instructional content. Also trigger when a user says things like "help me document this" or "turn this into a tutorial." Do NOT wait for the user to explicitly say "use the tutorial skill" — if there's a tutorial to be made, use this skill automatically.
---

# Tutorial Generator

Produces structured AI workflow/tool tutorials in a consistent format and publishes them to Notion via MCP, with user approval before publishing.

---

## Phase 1: Information Gathering

Before writing anything, assess what you know. A complete tutorial requires:

**Required inputs:**
- **Topic / title** — what is the tutorial teaching?
- **Target audience** — who is this for? (e.g., SAFe practitioners, enterprise leaders, AI beginners)
- **Tools / platforms involved** — what does the reader need access to?
- **The workflow or process** — the actual steps being taught, at a high level
- **Goal / outcome** — what will the reader have built or accomplished by the end?

**Optional but useful:**
- Links to tools, docs, or resources
- Known pitfalls or caveats worth flagging
- Any steps that need extra explanation

### If information is incomplete:

Ask ALL missing questions at once in a single message. Group them logically. Do not ask one question and wait — surface everything upfront. Use a numbered list format so the user can answer each one clearly.

Example prompt structure:
> "Before I write this tutorial, I need a few details. Please answer as many as you can:
> 1. Who is the intended audience?
> 2. What tools or platforms will they need?
> 3. Walk me through the steps at a high level — what does the reader actually do?
> 4. What's the end result they'll have when they're done?
> 5. Any links, tips, or gotchas I should include?"

---

## Phase 2: Write the Tutorial

Once you have enough information, produce the tutorial using this exact structure:

---

### Tutorial Structure

#### Title
Clear, action-oriented. Format: **"How to [Accomplish X] with [Tool/Method]"**

---

#### What You'll Need
A bulleted list of everything required before starting:
- Tools (with links where possible)
- Access / accounts / permissions
- Prior knowledge or prerequisites
- Any files, templates, or assets

---

#### Introduction
Two to three short paragraphs:
1. **Current state** — describe the problem, gap, or manual process the reader likely faces today
2. **Future state** — what this tutorial enables them to do instead
3. **Why it matters** — one sentence on the real-world impact or benefit

Keep it grounded and direct. No fluff. No hedging.

---

#### What You'll Build
A bulleted list of 4–7 items that previews exactly what the tutorial covers. Each bullet = one clear deliverable or action. This acts as a quick scannable overview so the reader knows what they're committing to.

Example format:
- Set up [Tool X] with the right configuration
- Build a prompt that [does Y]
- Connect [Tool A] to [Tool B] via [method]
- Export the output to [destination]

---

#### Step 1 through Step N

Each step follows this pattern:

**Step [N]: [Short Action-Oriented Title]**

[1–2 sentences: what to do and what happens when you do it correctly]

> 💡 **Tip:** [One practical tip, common pitfall to avoid, or clarifying caveat — kept to one sentence]

Rules:
- Steps are numbered sequentially — never skip or combine steps that represent distinct actions
- Each step title starts with a verb (Configure, Open, Paste, Click, Set, Connect, Run)
- The tip is optional — only include if there's something genuinely useful to say
- Do not over-explain. Moderate detail: action + outcome + one tip if warranted

---

## Phase 3: Pre-Publish Review

Before pushing to Notion, present the full tutorial in chat and ask:

> "Here's the tutorial. Ready to publish this to Notion? If so, let me know which page or database you'd like it added to — or I can create a new page at the top level."

**Do not publish until the user explicitly approves.**

---

## Phase 4: Publish to Notion

Once approved, use the Notion MCP to create the page.

**Page structure to create:**
- Title = tutorial title
- Use Notion heading blocks for each section (H2 for major sections, H3 for steps)
- Use bulleted list blocks for "What You'll Need" and "What You'll Build"
- Use paragraph blocks for body text
- Use callout blocks for tips (💡 icon)
- Use divider blocks between major sections

**Target location:** Use whatever the user specifies. If they say "top level," create it as a root page. If they name a database or parent page, place it there.

After publishing, share the Notion page URL with the user.

---

## Tone & Voice Guidelines

- Declarative and prescription-forward — tell the reader exactly what to do
- No hedging ("you might want to," "consider," "it's possible that")
- Assume a capable reader who doesn't need hand-holding on basics
- AI-native context: assume familiarity with prompting concepts, but explain tool-specific steps fully
- Short paragraphs. Active voice. Present tense.
