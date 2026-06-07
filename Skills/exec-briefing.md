[exec-briefing.md](https://github.com/user-attachments/files/28681271/exec-briefing.md)
---
Skill: exec-briefing
Purpose: Convert raw situation context into a 1-page, decision-first executive brief that any senior leader can read in 90 seconds and act on
Trigger: "Turn this context into an exec briefing"
Expected output: Recommendation → Situation → What's at stake → 3 options → Decision required by [date] — under 250 words
Tested on: Claude Sonnet 4.6
Built: June 2026
---

## Why I Built This

Senior leaders don't read situation reports. They read decisions. Every time I had a complex deal
situation, an internal escalation, or a resource request to put in front of leadership, I was writing
context-first — explaining everything before getting to the point. The result: follow-up questions,
delayed decisions, and briefings that got skimmed. This skill forces the structure I now use for any
executive communication: lead with the recommendation, earn the context, close with a specific ask.

## Methodology

The decision-first principle is the entire methodology. Executives are operating with partial
attention and high cognitive load. If your first sentence is context, you've lost them before they
reach your ask. If your first sentence is a recommendation, they read everything else as supporting
evidence — which is how they actually think.

This skill works for three audiences:
- **Internal leadership** — escalations, resource requests, deal strategy decisions
- **Client executives** — any situation requiring a CXO to make a decision on your deal
- **Anyone who reads fast** — which is everyone you actually need to influence

The structure is non-negotiable: Recommendation → Situation → Stake → Options → Decision required.
Everything else is commentary.

## Worked Example — From a Live Deal

**Context supplied (raw):** Enterprise solution deal, 50 CR, 5 years. POC complete. CXO access
established. Competitor (SaaS) meeting client CEO weekly. Our CEO has not built executive
relationship. Client has three concerns: build risk, commercials, lack of internal owner. Cost of
delay: narrative consolidates around competitor.

**Output (condensed):**

> **RECOMMENDATION:** Approve two parallel actions by end of this week — a revised commercial with
> phased structure and a committed CEO outreach plan with a named method and date.
>
> **SITUATION:** A 50 CR, 5-year deal is at risk after a year of investment. POC is done and CXO
> access is established, but the client CEO is meeting the competitor weekly while our executive
> relationship at that level hasn't been built. Three active objections: build risk, commercial
> perception, competitor's existing product.
>
> **WHAT'S AT STAKE:** Without intervention in the next 30 days, the client's internal narrative
> consolidates around the lower-risk option and one year of pipeline investment is lost.
>
> **OPTIONS:**
> 1. CEO direct outreach this week — fastest path to close the gap / risk of poor execution backfiring
> 2. Broker via existing CTO/CIO relationship — higher quality / slower
> 3. *(RECOMMENDED)* Commercial revision + narrative reframe immediately — removes two of three
>    objections regardless of which CEO path is taken / commercials alone won't win it
>
> **DECISION REQUIRED:** Approve Option 3 now. Commit to Option 1 or 2 with a named owner and
> date — not a standing intention.

**What the live test surfaced:** The structure made explicit that Option 3 needs to happen in
parallel regardless of the CEO path chosen — something the raw notes hadn't separated clearly.
Known gap: cost of inaction should be anchored numerically before use in an actual leadership meeting.

## How to Use

**Trigger:** "Turn this context into an exec briefing"

**Inputs needed:**
- The situation in raw form — paste notes, an email thread, whatever you have
- What decision is needed (be specific — "a decision on X", not "guidance")
- When the decision is needed by
- Consequence of delay or inaction

The rawer the input, the more the skill earns its keep.

## What Good Output Looks Like

Under 250 words. Recommendation is the first sentence. A reader who skips everything except the
recommendation and the "Decision Required" line should still understand exactly what is being asked
of them and by when. No passive voice. No jargon. Every option has exactly one benefit and one risk.

## Known Failure Modes

- **Vague "decision needed" input** — if you input "need leadership guidance," you get a vague
  brief. The decision must be specific before the skill fires: "approve X" or "choose between Y
  and Z."
- **Missing cost of inaction** — the most common omission; the "What's at stake" section becomes
  a restatement of the situation. Always provide a consequence — ideally quantified.
- **Options that aren't real options** — Claude will generate three options; review them. If they're
  not genuinely different paths, push back and ask for more distinct alternatives.
- **Recommendation buried or softened** — if the output leads with context rather than
  recommendation, the structure has failed. Reject and re-run with explicit instruction to lead
  with recommendation in sentence one.

---

## SKILL IMPLEMENTATION

```
You are a chief of staff with expertise in executive communication.

Context:
[PASTE THE SITUATION — raw notes, email threads, deal update, whatever you have]

Decision needed: [WHAT SPECIFICALLY NEEDS TO BE DECIDED OR APPROVED]
Decision needed by: [DATE]
Consequence of delay or inaction: [WHAT HAPPENS IF NOTHING IS DECIDED — quantify if possible]

Produce a 1-page executive briefing in this exact structure:

RECOMMENDATION: [What you recommend — 1 sentence. This is the first sentence of the document.]

SITUATION: [What is true right now — 2 sentences maximum]

WHAT'S AT STAKE: [The cost of inaction or delay — 1 sentence, specific]

OPTIONS:
1. [Option name]: [What it involves] — Benefit: [X] / Risk: [Y]
2. [Option name]: [What it involves] — Benefit: [X] / Risk: [Y]
3. [RECOMMENDED] [Option name]: [What it involves and why this one wins]

DECISION REQUIRED: [Specific approval or choice needed] by [DATE]

Rules:
- Under 250 words
- Recommendation is sentence one — not after context
- No jargon, no passive voice
- Every option must be a genuinely different path — not variations of the same idea
- If cost of inaction is not quantified in the input, flag it as a gap in the output
```
