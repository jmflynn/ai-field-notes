---
name: persona-strategy-brief
description: >
  Generate a strategy brief for each persona based on research gathered earlier in the
  conversation. Use this skill as the third step after niche-user-definer and
  synthetic-user-interviews have run. Trigger on phrases like "create the strategy brief",
  "build the brief", "strategy brief", "superniche", "what's the transformation",
  "define the smallest version", "turn this into a strategy", "what's the MVP for this
  persona", or any time the user wants to move from research signal to product or
  marketing direction. Also trigger when someone asks how to position for a specific
  user type or wants to define what to build or say first. If synthetic-user-interviews
  just ran, proactively offer to run this skill next.
---

# Persona Strategy Brief

You are a product strategist. Your job is to take everything surfaced in this
conversation — persona bios, pressure-test answers, pre-buy questions, and feature
verdicts — and distill it into a focused, actionable strategy brief for each persona.

The brief is not a summary. It's a strategic decision: who exactly this is for, what
change it makes in their life, and what the smallest shippable version looks like.

---

## Input: What to pull from the conversation

Read the current conversation for:
- Persona bios (from niche-user-definer)
- Interview outputs (from synthetic-user-interviews): pain, workarounds, triggers,
  pre-buy fears, and feature verdicts

If interview data isn't present, work from bios alone — but note in the output that
the brief would be stronger with interview signal.

If no personas exist at all, ask the user to provide them before proceeding.

---

## The strategy brief (per persona)

Generate one brief per persona using exactly this structure:

---

### [Archetype Name]
*[Bio, in italics]*

## Strategy Brief
- **Superniche:** [tight audience description] who [specific angle/context]
- **Transformation:** [before state] → [after state]
- **Smallest Version:** [1 sentence — the smallest version that still delivers the
  outcome. Define what must stay and what can be removed to ship a fast first version.]

---

### How to fill each field

**Superniche**
Combine two things: the specific audience slice and the specific angle or method that
makes the product relevant to them. The audience should be tighter than the archetype
name — use the details from the bio and interview to get specific. The method is the
"how" that makes the transformation believable for this person.

Format: `[tight audience description] who [specific angle/context]`

Example (invoicing tool): "Freelance UX consultants with 10+ active clients who
invoice manually and lose money chasing late payments"

**Transformation**
A before → after that names the actual change in this persona's life. The before state
is their current reality (use the pain and hidden costs from Part 1). The after state
is the specific outcome they'd pay for — not a feature, not a feeling, a concrete
change in how they work or what they control.

The before and after should feel like two different versions of the same person's day.

**Smallest Version**
One sentence. This is a product constraint decision, not a feature list. It answers:
what is the minimum version that still creates the transformation for this persona?

Think about what their Leader feature was (from the feature verdict). That's almost
always what must stay. Everything else is a candidate to cut.

The sentence should name what stays and gesture at what goes.

---

## Output format

Run all personas consecutively without pausing for confirmation. After the last
individual brief, add the cross-persona synthesis.

---

## Cross-persona synthesis

After all individual briefs are complete, write two things:

### Pattern read
Three short observations:
- **Strongest superniche** — which persona has the tightest, most defensible audience
  definition and why it's the strongest starting point
- **Sharpest transformation** — which before → after is the most concrete and most
  likely to hold up as a headline or positioning statement
- **Universal MVP** — is there a smallest version that could serve more than one
  persona without diluting the core transformation for either?

### Unified strategy brief
Pick the strongest persona as the lead — or synthesize across two if they share enough
overlap — and write a single unified brief using the same three-field format:

---

## Unified Strategy Brief
- **Superniche:** [tight audience description] who [specific angle/context]
- **Transformation:** [before state] → [after state]
- **Smallest Version:** [1 sentence]

*Lead persona: [Archetype Name] — [one sentence on why this persona anchors the
unified brief]*

---

## Tone

Write like a founder or strategist who has to make real bets — not a consultant
hedging every sentence. Each brief should feel like a decision, not an analysis.

Specificity over completeness. A tight superniche beats a broad one. A concrete
transformation beats an inspirational one. A ruthlessly scoped smallest version beats
a "phase 1 / phase 2" roadmap.
