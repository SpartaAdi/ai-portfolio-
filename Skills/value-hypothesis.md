[value-hypothesis.md](https://github.com/user-attachments/files/28384829/value-hypothesis.md)
---
Skill: Value Hypothesis
Purpose: Convert raw discovery notes into a defensible, formula-based value hypothesis
linking client pain to quantified business outcome — before writing a proposal
Trigger: "Build a value hypothesis from these notes"
Expected output: Formula-based hypothesis + confidence rating + assumptions made +
gaps to close + one number to verify before proposal
Tested on: Claude Sonnet 4.6
Built: May 2026
---

## Why I Built This

The gap between a discovery call and a proposal is where deals get lost. Without a
structured hypothesis, proposals either over-promise (inventing numbers to sound
compelling) or under-deliver (vague outcomes that don't justify the spend). Both kill
deals — one at delivery, one at sign-off.

My last three proposals at [YOUR COMPANY] all promised real outcomes:
- StarRocks POC → board-ready infrastructure decision with verified cost and performance
  delta vs Redshift
- Application modernisation → RPA ticket processing from 10 minutes to 2 minutes,
  improved SLA compliance, penalty reduction
- AWS consumption discount → committed 3-year spend with partner discount delivering
  measurable IT cost savings

Each of those outcomes existed in my head during the call. This skill forces them onto
paper — with assumptions surfaced and gaps named — before a single proposal line is
written.

---

## Methodology

The core problem in value hypothesis construction is almost always one of two things:
**no numbers** (the prospect described pain but gave no data) or **vague scope** (hard
to tell what's actually being asked for). Both lead to the same failure: a proposal built
on assumptions the client never validated.

This skill is designed to handle both failure modes explicitly. Claude is instructed to:
- Never invent specific figures — use ranges and flag them as estimates
- Surface every assumption made to fill a data gap
- List scope gaps that must be closed before the hypothesis can go into a proposal
- Return a confidence rating based on the quality of discovery notes, not the size of
  the opportunity

The output is not a proposal — it is a pre-proposal stress test. If the hypothesis comes
back Medium or Low confidence, that is the signal to go back to the prospect with one
targeted question before writing anything.

**The formula:** `[Client problem with quantified pain] → [[YOUR COMPANY] solution] →
[Quantified business outcome]`

This structure forces three things simultaneously: specificity on the problem,
clarity on what [YOUR COMPANY] actually does, and a defensible outcome the client can take
to their own stakeholders.

---

## How to Use

**Trigger:** `"Build a value hypothesis from these notes"`
**When to use:** Immediately after discovery — before proposal writing begins
**Run after:** `discovery-framework.md` post-discovery synthesis prompt
**Inputs needed:**
- Raw discovery notes (messy is fine — do not clean them up first)
- Company context (industry, size, [YOUR COMPANY] service)

```
You are a value-based selling expert specialising in cloud infrastructure,
application modernisation, and AI implementation.

Discovery notes:
[PASTE RAW DISCOVERY NOTES — messy is fine]

Company context:
- Industry: [INDUSTRY]
- Company size: [SIZE / HEADCOUNT / SCALE SIGNAL]
- [YOUR COMPANY] service: [SPECIFIC SERVICE BEING PROPOSED]

Produce a value hypothesis using this exact formula:
"[Client problem with quantified pain] → [[YOUR COMPANY] solution] →
[Quantified business outcome]"

Rules:
- Present the hypothesis as a single extractable sentence first, then
  expand with supporting detail.
- If discovery notes contain no numbers, use ranges and state explicitly
  that they are estimates. Never invent specific figures.
- If scope is vague, list each gap that must be clarified before this
  hypothesis can go into a proposal.
- Confidence: High / Medium / Low — based on quality of discovery notes,
  not on how compelling the opportunity looks.
- Assumptions made: list every gap you filled with an assumption to
  construct the hypothesis.
- One number that must be verified before this hypothesis goes into
  a proposal — name it explicitly.
- Suggest one follow-up question the seller can ask to unlock the most
  critical missing number.
- Do not present estimated figures without a confidence qualifier.
```

---

## What Good Output Looks Like

The hypothesis sentence should be specific enough that you could not use it for a
different company. A good one names the actual problem, the actual [YOUR COMPANY] engagement,
and an outcome range tied to a business event the client already cares about:

> *"[CLIENT]'s Redshift layer is delivering degraded query performance at scale while
> carrying unvalidated infrastructure cost — in a year where cost optimisation is a
> board-level mandate. [YOUR COMPANY] executes a time-boxed POC benchmarking StarRocks against
> production-equivalent Redshift workloads to produce a verified cost delta and
> board-ready migration recommendation before the Q3 board meeting — targeting an
> estimated 30–70% reduction in data infrastructure cost and 3–10x improvement in
> query latency."*

A weak one looks like: *"Client has data performance issues. [YOUR COMPANY] can help improve
performance and reduce costs."* If it could apply to any company, it's not a hypothesis
— it's a tagline.

The gaps section is as important as the hypothesis itself. If Claude returns 4–5 gaps,
that is useful information — it means the discovery call left too much on the table and
one targeted follow-up question will strengthen the proposal more than any amount of
writing.

**Live test result ([CLIENT] StarRocks POC, May 2026):** Hypothesis returned at Medium
confidence. Five gaps surfaced — the most critical being no Redshift spend figure and no
query latency baseline. Claude flagged an assumption most sellers miss: if [CLIENT] has
an AWS EDP with minimum spend commitments, the true cost of Redshift may be artificially
low and migration economics change entirely. That assumption would have broken a proposal
built without it.

---

## Known Failure Modes

**1. Hypothesis buries the formula in a paragraph**
Claude will sometimes produce a well-reasoned output where the actual hypothesis
sentence is embedded in a block of supporting text. The prompt now explicitly instructs
Claude to present the hypothesis as a single extractable sentence first. If it doesn't —
ask Claude: *"Extract just the hypothesis formula sentence as a single standalone line."*

**2. Confidence inflated when opportunity looks large**
Claude tends to return Higher confidence on large, clearly-scoped deals — even when the
discovery notes are thin. The prompt explicitly anchors confidence to note quality, not
opportunity size. Always read the assumptions section: if there are more than 3
assumptions, the confidence rating should be Medium regardless of what Claude returns.

**3. Ranges presented without context**
"30–70% cost reduction" is a meaningless range without knowing what drives the variance.
Good output explains what determines where on the range the client lands. If Claude
returns a range without explaining the variance driver, ask: *"What determines whether
the outcome is at the low or high end of that range?"*

**4. Gaps listed without priority**
Claude will sometimes return 5–6 gaps of equal weight. Not all gaps are equal — one
missing number can make the entire hypothesis undefendable; another is nice-to-have.
The prompt asks for one critical number explicitly. If the gaps section doesn't have a
clear priority signal, ask Claude: *"Which single gap, if unresolved, would cause this
proposal to fail?"*

**5. Run on cleaned-up notes, not raw notes**
This prompt is designed to surface what's missing. If you clean up your notes before
pasting — filling in the blanks from memory, smoothing over vague answers — Claude
produces a higher-confidence output that doesn't reflect reality. Paste raw. Let Claude
find the gaps. That's the point.

---

## Worked Examples — From Real [YOUR COMPANY] Proposals

### Example 1 — Infrastructure POC (StarRocks vs Redshift)
**Outcome promised:** Board-ready infrastructure decision with verified performance delta
and TCO comparison — either unlocking estimated 30–70% cost reduction or confirming
current spend is justified.
**Key gap at hypothesis stage:** No Redshift spend figure. No query latency baseline.
**What unlocked it:** One follow-up question — *"Is your Redshift spend closer to $50K,
$200K, or $500K+ annually?"* — anchored the cost optimisation case without requiring
a full financial disclosure.

### Example 2 — Application Modernisation
**Outcome promised:** RPA ticket processing from 10 minutes to 2 minutes (5x improvement),
improved application uptime, escalation matrix functionality previously absent —
delivering SLA compliance improvement and measurable penalty reduction.
**Key gap at hypothesis stage:** No current penalty cost quantified. No SLA breach
frequency data.
**What it taught:** Even when a number exists (10 min → 2 min), the business outcome
(penalty savings) still needs a baseline to be defensible. Speed improvement alone is
a feature benefit, not a value hypothesis.

### Example 3 — AWS Consumption Discount
**Outcome promised:** Committed 3-year AWS spend with partner + AWS discount delivering
quantified IT cost savings against current consumption baseline.
**Key gap at hypothesis stage:** None — this is the easiest hypothesis to build because
the number (discount %) is known before the proposal. Lesson: infrastructure commercial
proposals are easier to hypothesise than transformation proposals because the outcome
is the discount, not a downstream business result.
