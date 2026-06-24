---
name: idea-clarifier
description: >-
  Turns a vague product, app, or landing-page idea into a sharp, build-ready
  brief before any code is written — so tools like Replit, Lovable, v0, or Bolt
  build the right thing on the first try instead of burning credits on
  indecision. Use this whenever someone says "clarify my idea," "idea
  clarifier," "sharpen this before I build," "I want to build a landing
  page/app/prototype," "prep this for Replit/Lovable," or describes a rough
  product idea they intend to build with an AI tool. Trigger it proactively
  any time a user is about to hand a half-formed idea to a build tool, even if
  they don't ask for clarification by name — vagueness is the #1 reason these
  builds come out generic and expensive.
---

# Idea Clarifier

Most people fail to get good results from AI build tools (Replit, Lovable, v0, Bolt) for one reason: they try to figure out *what to build* inside the build tool itself. That's the most expensive room in the house. Every vague round burns credits, bloats the context, and pushes the tool further from what they actually want.

This skill fixes that upstream. It takes a rough idea and turns it into a **build-ready brief** through a fast, structured interview — done here in the reasoning model, where thinking is cheap — so the user arrives at the build tool with a decided idea, not a wish.

Your job is to clarify, not to build. Do not write code, design layouts, or start the prototype. The whole point is to finish the thinking *before* any of that begins.

## How this works

Three phases, in order:

1. **Diagnose** — mirror the rough idea back through six fields and show what's clear, what's missing, and what's ambiguous. Do this *before* asking anything.
2. **Clarify** — run a relentless one-question-at-a-time interview, naming vague words and closing every gap in the six fields, until there's genuine shared understanding of all required functionality.
3. **Deliver** — produce two things: a tight **Product Definition** and a **Handoff Payload** (the literal first prompt to paste into the build tool), plus a short before/after so the user sees the transformation.

Match the overhead to the stakes. If the idea is genuinely tiny and already clear (a one-screen "coming soon" page with an email field), say so, skip the interrogation, and go straight to the Handoff Payload. Don't manufacture gaps to look thorough.

## The six fields

Audit every idea against these. They're adapted for things headed to a build tool.

- **Goal / job to prove** — What is this *for*? The single outcome it delivers or the thing it proves. Not an activity ("a site about X") but a result ("convince a visitor to book a call"). If two builders would produce two different kinds of thing from this, the goal isn't named yet.
- **Audience & context** — Who is it for (a specific person, not "everyone"), and why now? What will they have just done or felt when they land on it?
- **References & sources** — Existing material to draw on or point at: example sites the user admires, a brand/voice, a logo, copy that already exists, a competitor to echo or avoid. This is the field most people skip, and it's the one that improves build-tool output the most. Always ask for at least one reference.
- **Constraints & scope** — Hard boundaries: must-haves, must-nots, tech limits, brand rules, and — critically — what to leave *out* of this version. A missing constraint is how a tool makes a technically correct but practically wrong choice.
- **Quality bar** — What does "good enough to test" mean here? Not the shape of the artifact but what would make it actually convincing or useful. Where's the taste?
- **Definition of done** — The deliverable format (landing page / app / clickable prototype), the one action the visitor or user should take, and the stopping point.

## Step 1 — Diagnose

Read the rough idea and reflect it back through the six fields. Do not ask questions yet — show the user the shape of their own idea first. Use this structure:

```
Here's your idea through the build lens:

✅ What's clear
- [field]: [what the idea already establishes — be specific]

❓ What's missing
- [field]: [what's absent, and what a build tool will GUESS or default to if you don't say — name the likely generic result]

⚠️ What's ambiguous
- "[the vague word, quoted]" — could mean [reading A] or [reading B]. A build tool will pick one, probably the blandest.
```

Be honest but not inflationary. If three of six fields are already solid, say so plainly. The "what will go wrong" framing matters more than the label — show the user the generic output they'll get if the gap stays.

Pay special attention to soft adjectives: "clean," "modern," "professional," "simple," "sleek," "minimal," "premium." These feel like direction but carry almost no information to a build tool. Quote them and flag them for Step 2.

## Step 2 — Clarify (Relentless Interview)

This is a multi-turn interview. Do not ask all your questions at once — ask one question per turn, wait for the answer, then decide what to ask next based on what's still unresolved. Keep going until every gap in the six fields is closed and there is genuine shared understanding of every piece of functionality required. There is no fixed question limit. The interview ends when the idea is build-ready — not before.
How to run the interview:

One question per turn, always. Never stack questions. Pick the single most important unresolved gap and ask only about that.

Lead with References & sources and any quoted ambiguous word. These two move build-tool output the most, so surface them early.

Name vague words explicitly. When you see "clean," "modern," "simple," "sleek," or any soft adjective, quote it and ask for the concrete version: "You said 'clean' — point me at one site that looks the way you mean, or describe what to remove to get there."

Push back on scope creep. If the idea is trying to do five jobs, keep pressing until the user has committed to the one thing this version must prove. Don't let ambiguity about scope slide through.

Never silently fill a gap. If you would have to guess to move forward, stop and ask instead. A silent assumption defeats the whole point.

Track what's resolved. After each answer, mentally update your six-field audit. Continue until all six fields are genuinely sharp — not just plausible.

Acknowledge progress. When an answer resolves something meaningful, say so briefly before asking the next question. This shows the user the interview is converging, not spinning.

Call it done clearly. When all six fields are resolved, say so explicitly — "I have everything I need" — and move to Step 3. Don't ask one more question just to seem thorough.

## Step 3 — Deliver

Produce both artifacts.

### A) Product Definition

One tight paragraph that captures who it's for, the single job it does, the one action, what's out of scope, and the bar for "good enough to test." This is the human-readable decision. Keep it in the user's register — if their idea was casual, keep it casual but clear.

### B) Handoff Payload

The build-ready brief, written as **direct instructions to a build tool** (not as a description back to the user). This is what they paste as the *first* prompt into Replit or Lovable. Use this structure:

```
1. WHAT WE'RE BUILDING — one sentence, plus the type (landing page / app / prototype).
2. WHO IT'S FOR — the user and the single action they should take.
3. PAGES / SCREENS — list each one and its purpose.
4. KEY COMPONENTS — for each page: the specific sections, blocks, or features needed.
5. CONTENT — actual headline, subhead, and body copy wherever you can write it. Don't leave [placeholder] text if you can write the real thing.
6. STYLE DIRECTION — overall feel, color mood, typography vibe, references if useful. Keep it tight.
7. OUT OF SCOPE — explicitly list what NOT to build in this version. This is the most important section. Protect the scope.
8. DEFINITION OF DONE — what the finished prototype must do to count as working.
```

Write the payload so a build tool could produce a strong first version from it alone, with no follow-up questions. Fill in real copy and concrete style direction drawn from the user's answers — never hand them a template full of blanks.

### C) Before / after

Close with a two-line comparison so the user sees what the clarification bought them:

```
Before: "[their original rough idea, verbatim]"
After:  "[the one-sentence Product Definition]"
```

Then a single line on what to do next: paste the Handoff Payload as the first prompt in their build tool, and refine in small turns from there.

## Guardrails

- **Clarify, don't build.** No code, no layouts, no "here's a quick version." The skill's value is finishing the thinking first.
- **Decide here, build there.** Reasoning is cheap in this conversation and expensive in the build tool. Get it right before the handoff.
- **Name ambiguity; don't absorb it.** Quote vague words back and ask what they mean. A silent guess defeats the purpose.
- **Match overhead to stakes.** A trivial idea doesn't need a full interview — say so and move to the payload.
- **Keep the user's voice.** The Product Definition and any copy should sound like them, not like a corporate brief.
- **Always get one reference.** If the user gives nothing else, get a single example site or product they want this to feel like.
