---
name: client-research-brief
description: Run a rapid 3-step client research workflow on any brand before a sales call, pitch, or training engagement. Trigger this skill whenever the user says "research this client," "prep me for this call," "I need to get up to speed on [brand]," "run the Wikipedia workflow," "research [company name]," or any phrase indicating they need to quickly orient on a new brand, account, vertical, or company. Takes a brand name and URL (plus optional competitor URLs) and produces a narrative research brief with a structured handoff payload for downstream skills. Always trigger this skill proactively when a company name and URL are mentioned together with any intent to research, prepare, or get oriented.
---

# Client Research Brief

A rapid 3-step brand research workflow that takes you from zero to oriented before a call, pitch, or engagement. Runs natively in Claude using web search, then produces a narrative brief plus a structured handoff payload for the Idea Council skill.

---

## Inputs Required

Before running, confirm you have:
- **Brand name** and **primary URL** (required)
- **1–2 competitor URLs** (optional but strongly recommended for Step 3)

If the user hasn't provided a URL, ask for it before proceeding. If no competitor URLs are given, note this and proceed — Claude will identify likely competitors during research.

---

## Workflow

Run all three steps in sequence. Each step is a distinct research pass using web search. Keep each sweep efficient — one focused pass per step, not an exhaustive crawl.

---

### Step 1: Category Snapshot

**Research goal:** Establish the three marketing fundamentals — who is the customer, how is the product positioned, and what problem is being solved.

**What to fetch/search:**
- Primary brand URL
- Any provided competitor URLs
- Search: `[brand name] positioning target customer`

**Output (narrative paragraphs):**

Write three short paragraphs:

1. **Customer Persona** — A sketch of the target customer: demographics, psychographics, motivations. Write as if handing this to a strategist seeing the market for the first time.
2. **Product & Positioning** — What the product is and how it's positioned in 1–2 sentences. Plain language, no marketing fluff.
3. **Core Problems Solved** — The specific frustrations or gaps this product addresses for that customer.

---

### Step 2: Customer Pressure-Test

**Research goal:** Break open the persona. Go beyond who the customer is — find what keeps them up at night, what tasks they resent, and what costs them time or money they'd never admit in a survey.

**What to fetch/search:**
- Search: `[customer type from Step 1] pain points challenges frustrations`
- Search: `[industry] inefficiencies time cost`

**Output (narrative paragraphs, with embedded answers):**

Write a short section that weaves answers to these four questions into connected prose — not a list:

- What is their biggest daily frustration?
- What manual tasks do they hate?
- What troubles them at night?
- What costs them time or money?

The tone should feel like a strategist's field notes, not a slide deck.

---

### Step 3: Competitive Gap

**Research goal:** Map the competitive landscape, surface messaging gaps, and test whether the brand's differentiators are actually distinctive.

**What to fetch/search:**
- Search: `[brand name] competitors alternatives`
- Review any competitor URLs provided

**Output (mix of narrative and light structure):**

**Competitive Landscape**
One paragraph mapping the four competitor categories: Direct, Indirect, Category, and Status Quo. Name specific players where possible.

**Messaging Gaps**
One paragraph identifying where competitors are weak, silent, or generic in their positioning.

**Three Differentiators**

For each differentiator, follow this exact template — this feeds directly into the Idea Council handoff:

---

**Differentiator [#]:** *[What makes this brand stand out]*

**The Challenge:** *[What problem customers face without this differentiator]*

**The Value:** *[How this differentiator solves the challenge — use specific, emotionally resonant language]*

---

Write three differentiators total. Make them as distinctive as possible. If two brands say the same thing, it doesn't belong here.

---

## Output Assembly

After all three steps, assemble the full brief in this order:

1. **Brief header** — Brand name, URL, date, one-sentence "what this company does" for orientation
2. **Step 1: Category Snapshot** (narrative paragraphs)
3. **Step 2: Customer Pressure-Test** (narrative field notes)
4. **Step 3: Competitive Gap** (narrative + differentiator templates)
5. **Handoff Payload** (see below)

---

## Handoff Payload

At the very end of the brief, append a clearly marked block in this format. This is what the Idea Council skill will consume.

```
---
HANDOFF PAYLOAD — IDEA COUNCIL
Brand: [Brand Name]
URL: [URL]

CATEGORY SNAPSHOT SUMMARY:
[2-3 sentences capturing the customer persona, product positioning, and core problem solved — written as a strategist's quick orientation, not a list]

CUSTOMER PRESSURE-TEST SUMMARY:
[2-3 sentences capturing the sharpest insights from the pressure-test — what keeps them up at night, where they're bleeding time or money, and the emotional gap driving their behavior]

DIFFERENTIATOR 1:
Unique Differentiator: [one sentence]
The Challenge: [one sentence]
The Value: [one sentence]

DIFFERENTIATOR 2:
Unique Differentiator: [one sentence]
The Challenge: [one sentence]
The Value: [one sentence]

DIFFERENTIATOR 3:
Unique Differentiator: [one sentence]
The Challenge: [one sentence]
The Value: [one sentence]

STATUS: Ready for Idea Council
---
```

Keep each field to one tight sentence. This payload should be clean enough that the next skill can parse it without any additional cleanup.

---

## Tone & Style Guidelines

- Write in narrative paragraphs, not bullet points (except where the template explicitly calls for structure)
- Plain language — no marketing fluff, no jargon unless it's industry-specific and necessary
- Voice of a strategist's field notes: confident, curious, and direct
- The brief should feel like a human wrote it after doing real research, not like an AI summarized a Wikipedia page
- Target length: 600–900 words for the brief body, plus the handoff payload

---

## What This Is (and Isn't)

This workflow gets you from zero to oriented fast. It is a jumping-off point, not a substitute for deeper research. The real value is the questions it gives you to ask next — and the three differentiators it hands to the Idea Council to pressure-test and push further.
