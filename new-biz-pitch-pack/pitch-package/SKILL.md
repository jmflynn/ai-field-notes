---
name: pitch-package
description: Take a winning approach from the Idea Council and build a complete Pitch Package — one-liner, Product Hunt listing, 30-second strategist pitch, three tweet angles, and a full landing page copy deck. Trigger this skill whenever a handoff payload from the idea-council skill is present, or when the user says "build the pitch package," "write the pitch," "create the assets," or "let's build the deck." Always trigger proactively when an idea-council handoff payload is visible in the conversation.
---

# Pitch Package

Takes the winning approach from the Idea Council and generates five fully written, ready-to-use marketing assets. All assets are written in the tone and creative direction of the winning approach — not a generic house voice.

---

## Step 0: Intake

Read the handoff payload from the idea-council skill. You need:

- **Brand name and URL**
- **Category snapshot summary** — who the customer is, what the product does
- **Customer pressure-test summary** — the emotional terrain, the pain, the gap
- **Winning differentiator** — the Unique Differentiator, Challenge, and Value
- **Winning approach** — the Name, Angle, and Execution

If no payload is present, ask the user to paste it or run the Idea Council first.

Before writing anything, internalize the **tone brief**:

> The winning approach's creative direction is the voice for every asset in this package. If the approach is minimal and declarative, the copy is minimal and declarative. If the approach is emotionally charged, the copy leans into that. Never default to generic brand voice — let the winning idea set the register.

---

## The Five Assets

Produce all five in sequence. Label each clearly. No preamble between assets — move directly from one to the next.

---

### Asset 1: One-Liner

**Constraints:**
- Under 12 words
- Billboard test: if you couldn't read it at 60mph, rewrite it
- The sentence that makes someone stop scrolling
- No brand name required — this is the idea, not the introduction
- No adjectives that every competitor could also use (fresh, healthy, convenient, easy)

**Tone:** Match the winning approach. If the approach is blunt and spare, the one-liner is blunt and spare. If the approach leans emotional, the one-liner earns it.

**Format:**
```
ONE-LINER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[The line]
```

---

### Asset 2: Product Hunt Listing

**Components:**

**Tagline** — One sentence, under 60 characters. The one-liner's more specific sibling. Names what the product does without feature-listing it. Should feel like a category claim.

**Description** — 2-3 short paragraphs. Written for a skeptical, smart audience that's seen a hundred product launches. Leads with the problem or the insight, not the product. Earns the feature mention after the reader is already nodding. Ends with a clear statement of what makes this different. No bullet points.

**Format:**
```
PRODUCT HUNT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Tagline: [Under 60 characters]

Description:
[Paragraph 1 — problem or insight]

[Paragraph 2 — what it does and why it works]

[Paragraph 3 — the differentiator, plainly stated]
```

---

### Asset 3: 30-Second Pitch

**Context:** This is delivered by a strategist at the top of a client review meeting. It's not a read-aloud script — it's written to be said. The person delivering it is smart, confident, and not selling. They're orienting.

**Structure:**
1. **The problem** — Name the real pain. Not the category problem — the specific, felt experience of the customer. 1-3 sentences.
2. **The insight** — The thing most brands in this category are missing or getting wrong. 1-2 sentences.
3. **The approach** — What this creative direction does differently. Not "our product does X" — "here's the angle we're taking and why." 2-3 sentences.
4. **The close** — One sentence. What this unlocks for the brand if it commits to this direction.

**Tone:** Conversational, not formal. Short sentences. No jargon. Written as if the strategist is thinking out loud with the room, not reading from a deck.

**Format:**
```
30-SECOND PITCH
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[The pitch, written as spoken word — paragraph form, no headers]
```

---

### Asset 4: Three Tweet Angles

**Three required angles — one each:**

**Angle A: Problem/Solution**
State the problem in plain, recognizable terms. Pivot to the solution without overselling it. The reader should feel like they just had a small realization. Under 280 characters.

**Angle B: Before/After**
Contrast the customer's life before and after — but avoid the obvious framing ("Before: chaos. After: calm."). Find the specific, unexpected detail that makes the contrast feel real. Under 280 characters.

**Angle C: The Non-Obvious Insight**
Say the thing that's true but that the brand would normally be too polished to say. The uncomfortable observation. The counterintuitive claim. Under 280 characters.

**Format:**
```
THREE TWEET ANGLES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
A / Problem-Solution:
[Tweet]

B / Before-After:
[Tweet]

C / Non-Obvious Insight:
[Tweet]
```

---

### Asset 5: Landing Page Copy Deck

Use the landing-page-structure framework. Write all nine layers in sequence. Tone tracks the winning approach throughout — do not shift to generic marketing copy at any layer.

**Layer selection:** Write all layers (1, 2, 3, 5, 6, 7, 8, 9, 10). This is a complete copy deck.

**Social proof (Layer 6):** Write directionally accurate placeholder social proof — the kind of quote, stat, or proof point that would be true based on what we know about this product and customer. Label it `[DIRECTIONAL — replace with actual proof]` so the reader knows it's illustrative, not fabricated.

**Path variant:** Path A (Traditional Conversion) — CTA drives toward trial or subscription.

**Layer-by-layer tone notes:**
- **Layer 1 (Hero):** The winning approach's creative direction at full expression. This is where the idea lives.
- **Layer 2 (Outcome Anchoring):** End-state only. 5 words or fewer per outcome. No features.
- **Layer 3 (Problem Validation):** Blunt and specific. Name the daily frustration, not the category problem.
- **Layer 5 (Value Translation):** Benefits first, features second. Max 3. Never lead with the feature.
- **Layer 6 (Social Proof):** Directional. Label as placeholder. Feels earned, not invented.
- **Layer 7 (Path to Success):** 3 steps. Make it feel effortless.
- **Layer 8 (Differentiation):** Reason list format (up to 6 short, skimmable reasons). Control the comparison.
- **Layer 9 (Objection Handling):** FAQ format. Address the hesitation underneath the question.
- **Layer 10 (Final CTA):** Short. Motivating. Repeat the CTA from Layer 1.

**Format:** Follow the landing-page-structure output format exactly, with section headers and separator lines.

```
LANDING PAGE COPY DECK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

LAYER 1: RELEVANCE & EMOTIONAL BUY-IN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Eyebrow: [Audience lock-in]
Headline: [Emotional outcome]
Subheadline: [Specificity + credibility]
CTA Button: "[Action]"
Social Proof: [Directional stat or logo row — label as placeholder]
Visual Direction: [After-state description]


LAYER 2: OUTCOME ANCHORING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Section Headline: [Optional]
Dream Outcome 1: [≤5 words]
Dream Outcome 2: [≤5 words]
Dream Outcome 3: [≤5 words]


LAYER 3: PROBLEM VALIDATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Problem Headline: [Blunt, direct]
Symptom 1: [Recognizable daily pain]
Symptom 2: [Recognizable daily pain]
Symptom 3: [Recognizable daily pain]


LAYER 5: VALUE TRANSLATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Benefit 1 Headline: [Outcome]
Benefit 1 Copy: [Feature explanation, 1-2 sentences]

Benefit 2 Headline: [Outcome]
Benefit 2 Copy: [Feature explanation, 1-2 sentences]

Benefit 3 Headline: [Outcome]
Benefit 3 Copy: [Feature explanation, 1-2 sentences]


LAYER 6: SOCIAL PROOF
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Directional proof — quote, stat, or both. Label: DIRECTIONAL — replace with actual proof]


LAYER 7: PATH TO SUCCESS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Section Headline: [Make it feel simple]
Step 1: [The action]
Step 2: [The process, simplified]
Step 3: [The outcome]


LAYER 8: DIFFERENTIATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Section Headline: [Why this, not that]
Reason 1: [Short, skimmable]
Reason 2: [Short, skimmable]
Reason 3: [Short, skimmable]
Reason 4: [Short, skimmable]
Reason 5: [Short, skimmable]
Reason 6: [Short, skimmable]


LAYER 9: OBJECTION HANDLING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Q: [Hesitation framed as question]
A: [Direct, reassuring answer — 1-3 sentences]

Q: [Hesitation framed as question]
A: [Direct, reassuring answer — 1-3 sentences]

Q: [Hesitation framed as question]
A: [Direct, reassuring answer — 1-3 sentences]


LAYER 10: FINAL CONVERSION PUSH
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Headline: [Short, motivating]
CTA Button: "[Same as Layer 1]"
```

---

## Copy Principles for This Skill

- **Tone tracks the idea, not the brand.** Every asset sounds like the winning approach, not a generic version of the brand.
- **Clarity over cleverness.** If a line is interesting but unclear, cut it.
- **No adjectives competitors could also claim.** Fresh, healthy, convenient, easy, delicious — if everyone says it, don't say it.
- **The problem before the product.** Every asset that has room to breathe leads with the customer's experience, not the brand's features.
- **Write the 30-second pitch to be said, not read.** Short sentences. Real words. No deck language.
- **Social proof is directional, not fictional.** It should feel like something that could be true and would eventually be sourced — not something invented to fill space.
