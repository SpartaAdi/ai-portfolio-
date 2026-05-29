[discovery-framework.md](https://github.com/user-attachments/files/28380658/discovery-framework.md)
---
Skill: Discovery Framework
Purpose: Generate a structured question bank and post-call synthesis for professional
services and AI implementation discovery calls
Trigger: "I'm prepping discovery with [company/role]"
Expected output: Question bank by stakeholder + question bank by mode + red flag signals
+ post-discovery synthesis prompt
Tested on: Claude Sonnet 4.6 (with web search enabled)
Built: May 2026
---

## Why I Built This

Discovery is where deals are won or lost — but without a framework, you default to the
same 5 questions every call and miss the signals that tell you whether a deal is real.
My earlier approach was instinct-led: I had 10 questions I'd rotate through depending on
who was in the room. Some were good. Some were pitches disguised as questions (a pattern
worth watching for — Q6 in my original list was Minfy's value proposition dressed up as
a discovery question, which closes down the conversation before you've heard the full
picture).

Building this skill forced me to separate discovery from selling. The questions in this
file are designed to surface information that changes how Minfy positions — not to
convince anyone of anything.

---

## Methodology

The question bank has two cuts — by stakeholder and by mode — and both are necessary for
different reasons.

**By stakeholder** ensures the right question goes to the right person. A VP Engineering
and a CEO are not interchangeable in a discovery call. The VP Engineering wants to talk
architecture, capacity, and technical constraints. The CEO wants to talk roadmap,
outcomes, and board commitments. Mixing these wastes the call and signals you haven't
done your homework.

**By mode** gives depth for follow-up. Professional Services questions and AI Discovery
questions serve different commercial outcomes — outsourcing an app development workstream
vs. implementing AI use cases are different buying decisions with different budget owners,
timelines, and success metrics. If the conversation starts going deep in one direction,
mode questions let you follow it without losing the thread.

**On MEDDIC:** My natural discovery instinct covers most of the MEDDIC framework —
Metrics (Q2, Q4), Economic Buyer (Q8), Decision Criteria and Process (Q8, Q9), and Pain
(Q1, Q3). The one element missing from my practice: **Champion** — identifying who inside
the prospect organisation is actively selling this engagement internally. A deal the CEO
wants but engineering resists will stall in procurement or fail in delivery. Champion
identification is now explicitly built into this skill.

**What never goes in:** I do not ask questions I already know the answer to from pre-call
research. Walking into a Unifocus call and asking "what cloud provider are you on?" when
Azure and AWS are both confirmed wastes credibility. Research first, discover second.

---

## How to Use

**Trigger:** `"I'm prepping discovery with [company/role]"`
**Inputs needed:**
- Company name and industry
- Decision-maker roles in the room
- Current engagement status (cold / warm / existing relationship)
- Minfy services being explored (Professional Services / AI / both)
- Discovery mode (PS only / AI only / both)

**Run after:** `pre-call-research.md` — never run discovery prep without the company
brief first. The brief tells you what you already know; discovery uncovers what you don't.

---

```
You are an expert B2B discovery coach with 15 years in enterprise technology sales,
specialising in cloud, AI implementation, and professional services.

Context:
- Company: [COMPANY NAME]
- Industry: [INDUSTRY]
- Decision-makers in the room: [ROLES]
- Current engagement status: [COLD / WARM / EXISTING RELATIONSHIP + CONTEXT]
- Minfy services being explored: [PROFESSIONAL SERVICES / AI CONSULTING / BOTH]
- Discovery mode: [PS ONLY / AI ONLY / BOTH]

Produce:

1. QUESTION BANK BY STAKEHOLDER (3 questions each)
For each stakeholder role provided. Questions must be specific to the company
context — no generic questions.

Technical Buyer (CTO / VP Engineering / IT Lead):
[3 questions: architecture, build capacity, technical constraints, AI readiness]

Business Buyer (CEO / COO / Business Head):
[3 questions: roadmap priorities, outsourcing appetite, budget authority, ROI
expectations, board commitments]

Financial Buyer (CFO) — include only if CFO is in the room:
[3 questions: ROI framework, cost justification, risk tolerance]

2. CHAMPION IDENTIFICATION QUESTIONS (2 questions)
Questions designed to surface who inside the organisation is advocating for
this engagement internally — the person who will sell it when Minfy is not
in the room.

3. QUESTION BANK BY MODE
Include only the mode(s) specified in the context above.

Professional Services Discovery (5 questions):
[Outsourcing scope, build vs buy philosophy, team capacity and velocity,
vendor experience, timeline and urgency driver]

AI Use Case Discovery (5 questions):
[AI maturity, POC history, data infrastructure readiness, governance
framework, implementation model preference]

4. RED FLAG SIGNALS TO LISTEN FOR (5 signals)
Signals that indicate deal risk, misalignment, or a prospect not ready to
buy. Be specific — not generic sales warnings.

5. POST-DISCOVERY SYNTHESIS PROMPT
A ready-to-use prompt the seller runs immediately after the call, pasting
raw notes, to extract:
- Key pain (in the prospect's words)
- Budget signal (confirmed / unconfirmed / blocker)
- Decision timeline and named trigger event
- Champion identified (yes / no / unclear)
- Recommended next step (specific, 5-business-day window)
- Deal risk rating (Green / Amber / Red)
- One thing to validate before sending a proposal

Keep all questions sharp and specific. Each question should surface
information that directly changes how Minfy positions its services.
Do not include questions that pre-call research already answers.
```

---

## What Good Output Looks Like

Questions are specific enough that you couldn't ask them at any company — they reference
the prospect's actual products, stack, or situation. A good technical buyer question for
a hospitality SaaS post-acquisition looks like: *"With the Knowcross acquisition — are
those modules sharing a unified data model with your original platform, or are there
integration seams an external team would need to navigate?"* A bad one looks like: *"What
does your current tech stack look like?"*

The post-discovery synthesis prompt should be runnable on raw, messy call notes — not
cleaned-up summaries. The output should tell you in under 3 minutes whether to write a
proposal or ask one more question first.

**Live test result (Unifocus, May 2026):** Stakeholder questions correctly anchored to
John Lockyer's COO background and PE board pressure. Red flags surfaced the Azure vs AWS
structural tension as a positioning risk — a signal that only appeared because pre-call
research was run first. Post-discovery synthesis prompt produced a usable deal risk
framework in one pass.

---

## Known Failure Modes

**1. Questions that are pitches in disguise**
The most common failure: a question that starts with "Are you open to working with a
partner who can bring X, Y, Z..." is not a discovery question — it's a pitch. Claude will
occasionally produce these, especially when you describe Minfy's capabilities in the
context field. Review every question: if it answers itself or leads the witness, cut it.

**2. Generic questions when context is thin**
If you give Claude minimal company context, it produces MEDDIC-by-numbers questions that
any rep could have written. Fix: always run `pre-call-research.md` first and paste 2–3
key signals from that brief into the context field. Specificity in → specificity out.

**3. Champion questions missing without explicit instruction**
Claude's default discovery frameworks (SPIN, MEDDIC) mention champion but rarely generate
questions that actually surface one. This is why Champion Identification is now its own
explicit section in the prompt — without it, Claude omits it.

**4. Red flags are theoretical, not commercial**
Claude will generate red flags that sound smart but don't tell you what to do. Good red
flags have an action attached: *"If you hear X — do Y."* Review the red flags output and
add a one-line response protocol to any that don't have one.

**5. Post-discovery synthesis run too late**
This prompt is designed to be run within 30 minutes of the call ending — while context
is fresh and notes are raw. Run it the next morning and you'll get a sanitised summary,
not a real deal signal. Set a phone reminder before every discovery call.

---

## Red Flags From Real Deals

**RF-1 — "We're exploring options" with no named scope** *(confirmed in practice)*
After 20 minutes, neither decision-maker can name a specific feature, module, or use case
they want help with. This is a curiosity meeting or internal ammunition-gathering — not a
buying meeting. In practice: the conversation stays high-level no matter how specific your
questions get. Response: propose a paid scoping engagement or deprioritise the account.

**RF-5 — AI interest is marketing-driven, not product-driven** *(confirmed in practice)*
AI use cases are described in terms of competitor moves, investor expectations, or press
positioning — not a specific operational problem with a measurable cost. In practice: the
conversation generates enthusiasm but no scope, no data owner, and no success metric.
Engagements without success metrics get cancelled at the first budget review. Listen for:
*"our competitors are doing AI," "investors expect it," "we want to be seen as AI-first."*
Response: ask for the operational problem behind the AI interest before scoping anything.
