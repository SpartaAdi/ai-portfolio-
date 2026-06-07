[decision-framework.md](https://github.com/user-attachments/files/28681949/decision-framework.md)
---
Skill: decision-framework
Purpose: Generate options you haven't naturally considered and stress-test the option you're already leaning toward — before you commit
Trigger: "Help me think through this decision"
Expected output: 5 options including unconventional ones · Stress-test of your leaning · Post-decision review structure
Tested on: Claude Sonnet 4.6
Built: June 2026
---

## Why I Built This

In high-stakes decisions, the problem is rarely that you have no options. It's that you generate
2–3 obvious paths, pick the one that feels most familiar, and move. What the framework forces that
normal decision-making skips: a fifth option that challenges an assumption you're making, and a
rigorous stress-test of the option you're already favouring — before you commit to it.

The moment that made this concrete: a live enterprise deal with multiple open levers. The instinct
was to activate all of them simultaneously. The stress-test surfaced that doing everything at once
signals vendor anxiety, not strength — and that sequence matters more than coverage. That reframe
came from running Step 2, not from the options themselves.

## Methodology

This skill has two distinct steps, and both need to run.

**Step 1 — Options Generation:** Forces five options including one conservative, one aggressive,
one unconventional, one obvious, and one that directly challenges an assumption you're making.
Most people naturally generate the middle three. The conservative and unconventional options are
where the framework earns its keep.

**Step 2 — Stress-Test (Critic Layer):** This is the same architecture as the Claude → Gemini →
Claude critic layer applied to decision-making. You state the option you're leaning toward. The
model presents the strongest possible case *against* it — the assumptions being made, risks being
underweighted, and second-order effects not yet considered. The goal is not to change your decision.
It is to ensure that if you proceed, you've done so with eyes open.

**The critic layer connection:** The stress-test in this skill is the same function as Gemini in
the three-agent pipeline — an adversarial critic that doesn't soften the challenge. If the output
feels like validation rather than genuine challenge, push harder or run it again.

## Type 1 vs Type 2 Decisions

Not every decision warrants this full framework. Apply it selectively.

| Type | Characteristics | Use framework? |
|---|---|---|
| **Type 1 — Irreversible** | High stakes, hard to undo, long consequences | Always |
| **Type 2 — Reversible** | Low stakes, easy to correct, short feedback loop | Optional |

Enterprise deal strategy decisions are Type 1. Drafting a proposal structure is Type 2.

## Worked Example — From a Live Deal

**Decision context:** Large enterprise deal with multiple open levers — CEO connect, commercial
revision, relationship activation through existing CXO contacts. Considering activating all
simultaneously.

**Leaning:** Try all options at the same time.

**What the stress-test surfaced:**
- Assumption being made: each lever operates independently and the client won't notice simultaneous
  pressure from multiple angles. Likely wrong — CXO layer talks to each other.
- Risk underweighted: lowering the commercial before the CEO relationship is built spends
  negotiating capital without the trust that makes the deal feel safe at the top.
- Second-order effect: simultaneous activation reads as vendor anxiety, not coordinated strength.
- Unconventional option not considered: do nothing on commercials for two weeks; focus everything
  on one outcome — the CEO meeting. Price negotiation is easier once the relationship at the top
  exists.

**Reframe:** Sequence matters more than coverage. All the options are valid — the question is which
one unlocks the others.

## Post-Decision Review Structure

Run this 30/60/90 days after any Type 1 decision.

| Checkpoint | Questions |
|---|---|
| **30 days** | Was the assumption I was making correct? What has changed since the decision? |
| **60 days** | Is the option I chose still the right one given what I now know? |
| **90 days** | What would I tell someone facing this same decision? What did the stress-test miss? |

## How to Use

**Trigger:** "Help me think through this decision"

**Inputs needed:**
- The decision and its context
- What's at stake if you get this wrong
- Whether it's reversible or not
- How long you have to decide
- The option you're currently leaning toward (for Step 2)

## What Good Output Looks Like

Step 1 produces five genuinely different options — not variations of the same idea. The
unconventional option should feel slightly uncomfortable; if it doesn't, it's not unconventional
enough. Step 2 produces a challenge that makes you pause — not reassurance. If the stress-test
feels like validation, the input wasn't specific enough about your leaning.

## Known Failure Modes

- **Options that are all variations of one idea** — "do X slowly / do X quickly / do X with a
  partner" are not three different options. Push Claude to generate paths that differ in direction,
  not just pace.
- **Stress-test that softens the critique** — the model defaults toward balanced output; push
  explicitly for the strongest possible case against your leaning, not a fair assessment.
- **Missing the unconventional option** — if all five options are things you'd already considered,
  the framework hasn't added value. Ask Claude to regenerate the fifth option with a different
  assumption challenged.
- **Running on Type 2 decisions** — wastes the framework on reversible low-stakes choices. Reserve
  it for decisions you can't easily undo.

---

## SKILL IMPLEMENTATION

```
You are a strategic advisor. Help me think through this decision rigorously.

Decision: [DESCRIBE THE DECISION AND CONTEXT IN FULL]
Stakes: [What is the cost of getting this wrong?]
Reversibility: [Can this be easily undone, or is it hard to reverse?]
Timeline: [How long do I have to decide?]

--- STEP 1: OPTIONS GENERATION ---

Generate 5 options I may not have fully considered. These must be genuinely different paths —
not variations in pace or degree of the same idea.

- One conservative option (protect downside, low risk)
- One aggressive option (maximise upside, higher risk)
- One unconventional option (challenges an assumption I'm likely making)
- The option most people in this situation would default to
- One option that directly questions whether I should be making this decision at all

For each: brief description · key benefit · key risk.

--- STEP 2: STRESS-TEST (CRITIC LAYER) ---

My current leaning: [STATE THE OPTION YOU ARE LEANING TOWARD]

Present the strongest possible case AGAINST this option.
Be rigorous. Do not soften the critique. Do not balance it with positives.

Focus specifically on:
- What assumptions am I making that may not hold?
- What risks am I underweighting?
- What second-order effects have I not considered?
- Is the sequence of my actions correct, or am I solving the wrong problem first?

The goal is not to change my decision — it is to ensure I proceed with eyes open.
```
