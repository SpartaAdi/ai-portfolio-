[pre-call-research.md](https://github.com/user-attachments/files/28378268/pre-call-research.md)
---
Skill: Pre-Call Research
Purpose: Generate a structured, intelligence-grade company brief before any client call — without reading long articles or annual reports
Trigger: "I have a call with [company]"
Expected output: 3-section brief (Company Pulse · Tech Signals · Opening Angle) + optional Company Vitals add-on for high-stakes meetings
Tested on: Claude Sonnet 4.6 (with web search enabled)
Built: May 2026
---

## Why I Built This

Before this skill, my pre-call research was ad hoc — I'd paste a company name and website
and ask Claude something like: *"We're pitching AI use cases to them — which ones would
land?"* I also had an earlier prompt built in Problem / Role / Deliverable format that
produced decent output but was too broad, too token-heavy, and optimised for reading rather
than for a 20-minute call prep window.

The real shift: I stopped asking Claude to tell me what to pitch and started asking it to
tell me what's happening at the company right now — so I could decide the angle myself.
That reframe changed the output quality entirely.

---

## Methodology

The skill is modular by design: a lightweight base prompt for every call, and a deeper
Company Vitals add-on for qualified opportunities worth 30 minutes of prep.

The reason is practical: a bloated single prompt wastes tokens, increases hallucination
risk, dilutes context relevance, and takes longer to run. More importantly, not every call
warrants the same depth — a first cold call and a scoped outsourcing evaluation require
different levels of intelligence. Base + add-on matches how I actually work, not how a
framework says I should.

---

## How to Use

### Base Prompt — Every Call
**Trigger:** `"I have a call with [company]"`
**When to use:** Any call — cold, warm, or follow-up
**Time to run:** ~3 minutes
**Inputs needed:**
- Company name
- Meeting context (who you're meeting, what the purpose is)
- Minfy service angle (what you're positioning)

```
You are a senior B2B sales intelligence analyst.

Company: [COMPANY NAME]
Meeting context: [ROLE MEETING WITH / PURPOSE]
Minfy context: [WHAT MINFY SERVICE IS RELEVANT]
Today's date: [DATE]

Produce a pre-call brief with exactly these three sections:

1. COMPANY PULSE (2–3 bullets)
Recent news, announcements, or signals from the last 90 days relevant to a
cloud/AI conversation. Prioritise information from the last 90 days only.

2. TECH SIGNALS (2–3 bullets)
Any public signals about their tech stack, infrastructure choices, or cloud
maturity — job postings, engineering blog, press. List ALL confirmed cloud
providers, not just the primary one.

3. OPENING ANGLE (1 bullet)
One specific, non-generic reason to open with — connecting a signal above
to a Minfy capability.

If you lack reliable information on any section, say so explicitly.
Do not fabricate.
```

---

### Deep Prep Add-On — Qualified Opportunities
**When to use:** Scoped meetings, outsourcing evaluations, enterprise accounts, renewal
conversations — any meeting where walking in underprepared has a real cost
**Run after the base prompt, in the same chat**
**Time to run:** ~5 minutes additional

```
Using publicly available information, produce a COMPANY VITALS section
to supplement the brief above.

Company: [COMPANY NAME]
Today's date: [DATE]

COMPANY VITALS:

LEADERSHIP
- Current CEO, CTO/CPTO, COO, CFO — name and tenure
- Any C-suite changes in the last 12 months?
Search for the most current role holders as of [DATE]. Do not rely on
cached or historical pages.

FUNDING & OWNERSHIP
- Last known funding round — amount, date, investors
- Current ownership structure (PE-backed, bootstrapped, public)?

FINANCIALS
- Latest available revenue or ARR (exact or estimated range)
- Any profitability signals (PAT, EBITDA) in press or filings

GROWTH SIGNALS
- Headcount trend (growing / flat / contracting)
- Geographic expansion or new market signals

Flag anything unverified. State explicitly when a number is an estimate.
Do not present estimated figures without a confidence qualifier.
```

---

## What Good Output Looks Like

The base brief should be readable in under 3 minutes and give you one specific opening
line — not a generic "we help companies like yours" angle, but something tied to a named
product launch, a hiring signal, or a stated strategic priority from the last 90 days.

The Company Vitals add-on should surface leadership names you can verify on LinkedIn in
60 seconds, an ownership signal that tells you who's driving the buy decision (PE sponsor
vs. founder vs. board), and at least one growth signal that connects to why they might
need Minfy now.

**Live test result (Unifocus, May 2026):** Base prompt produced a usable brief in one
pass — surfaced the AskAI product launch, ISO 27001 signal, and a specific RAG
infrastructure angle. Add-on correctly flagged Interim CFO status and PE ownership
(Riverside). With a direct recency query, Claude self-corrected on CEO (Moneesh Arora →
John Lockyer, promoted from COO March 2026).

---

## Known Failure Modes

**1. Year error in date stamp**
Claude occasionally outputs the wrong year (e.g. "May 29, 2025" instead of 2026).
Always include `Today's date: [DATE]` explicitly in the prompt.

**2. Stale leadership data**
Without a recency instruction, Claude defaults to well-indexed historical pages — not
current reality. In the Unifocus test, it returned a CEO who had already been replaced.
Fix: always include `Search for the most current role holders as of [DATE]` in the
leadership section. Always verify CEO/CTO names on LinkedIn before the call.

**3. Incomplete tech stack — stops at first confirmed signal**
Claude surfaced Azure for Unifocus but missed AWS entirely. It stops searching once it
finds a confirmed answer. The prompt now explicitly asks for *all* confirmed cloud
providers. Still: manually check engineering blog and recent job postings for stack
confirmation on high-stakes calls. For Minfy as an AWS Premier Partner, a missed AWS
signal is a positioning error, not a minor gap.

**4. Financial estimates presented without confidence flag**
Private companies have no public filings. Claude will sometimes state revenue estimates
without flagging them as inferred. The prompt now requires explicit confidence qualifiers.
Never cite an AI-generated revenue figure in a client meeting without a primary source.

**5. Wrong company matched on ambiguous names**
Common on companies with generic names or local subsidiaries. Always paste the company
website URL alongside the name when running the prompt, especially for Indian mid-market
companies.

---

## My Earlier Prompt (Archived — Superseded)

The prompt below was my previous approach. It's broader and produces a longer output
useful for annual report deep-dives — but too heavy for standard pre-call prep. Kept here
for reference.

```
Problem: Before client calls, I need a quick, structured summary of a company's
recent public activity, financials, leadership, and strategic priorities.

Role: You are a Senior Enterprise Research Analyst. Research the internet and
the client's public annual reports. Produce a well-structured, concise brief
readable in 15 minutes.

Deliverable: Bullet-pointed document covering —
1. Recent funding rounds — by whom, amount, date
2. Top clients
3. HQ location and total headcount
4. Revenue and profit over last 3 financial years
5. Current leadership — CEO, CTO, CIO, IT Head, CFO, Supply Chain Head
6. Annual report summary — strategic initiatives for current FY, cross-checked
   against internet evidence; flag initiatives with no public execution signal
7. Summary of company LinkedIn posts from last 1 month

Format: bold headings, bullet points, numbers and dates always, flag data gaps.
```

**Why superseded:** Too broad for a 10-minute prep window. Optimised for reading,
not for opening-angle identification. Single prompt — no modular flexibility.
Token-heavy with diminishing context relevance.
