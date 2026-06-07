[competitive-intel.md](https://github.com/user-attachments/files/28680350/competitive-intel.md)
---
Skill: competitive-intel
Purpose: Produce a structured competitive brief before any deal where a competitor is named — strengths, win conditions, likely planted objections, and the best response
Trigger: "Run competitive analysis on [competitor type]"
Expected output: Honest competitor strength assessment · Your win conditions in this specific deal context · Objections likely already planted · Best 2–3 sentence counter-response
Tested on: Claude Sonnet 4.6
Built: June 2026
---

## Why I Built This

Competitive situations move fast in enterprise cloud sales. A client mentions a competitor in passing
and you have 30 seconds to respond with something credible — or you lose the frame. I was either
over-preparing with generic research that didn't apply to the specific deal, or under-preparing and
reacting on instinct. This skill produces a structured brief in under two minutes: enough to walk into
any competitive conversation with a clear position, not a reactive one.

## Methodology

The goal is not to know everything about the competitor. It is to know three things fast: what they
genuinely do well so you don't dismiss them, where you reliably win so you lead with strength, and
what they've likely already said to this client so you're not surprised in the room.

The skill is built around one principle from real deal experience: **play on your own strength, not
the competitor's weakness.** Going negative in front of a client signals insecurity, puts them on the
back foot, and almost always backfires. The strongest competitive responses don't mention the
competitor at all. Name your strengths, anchor them in this client's situation, and let the
comparison be implicit.

## Competitor Quick-Reference

Built from real deal experience — not marketing material. Updated as deals close.

| Competitor Type | Where They Win | Where We Win | Honest Gap |
|---|---|---|---|
| **Distribution-tier partners** | Better margin mechanics via distribution model; more AWS funding levers; stronger EDP deal structuring | AWS relationship quality; customer intimacy; single-threaded deal ownership | Pure discount depth on large EDP deals — they can move faster commercially |
| **AI-native specialist partners** | AI-in-production case studies; specialist positioning; faster AI credibility signal | Full migration-to-production lifecycle; infrastructure foundation built before AI layer; end-to-end accountability | Recent AI production references — actively building this capability |
| **Multi-cloud / Microsoft partners** | Enterprise bundle play — productivity suite, AI services, and cloud in one commercial motion; single vendor to procurement | Pure-play AWS depth; no cross-cloud conflict; stronger on cloud-native migrations | Not applicable where customer is already Office-first |
| **Analytics-first cloud partners** | Price-competitive on analytics and AI workloads; aggressive credits to win new workloads | Dependent on AWS credit support to match — escalation path exists, but not a standalone win | Credit matching requires AWS involvement; not an independent motion |

> **Note on analytics-first competitors:** This is an honest dependency. When the deal is primarily
> analytics or AI workloads and price is the lever, the path to winning runs through AWS, not through
> an independent competitive argument. Document it accurately. Don't paper over it.

## Sources Checklist — In Order of Speed

Check these in sequence. Stop when you have enough for the call.

- [ ] **LinkedIn** (2 min) — recent posts, hires, case studies published in last 90 days
- [ ] **Their website / case studies page** (3 min) — which industries, which services, which badges they lead with
- [ ] **AWS Partner Network directory** (2 min) — competency badges, specialisations, program tier
- [ ] **G2 / Gartner Peer Insights** (3 min) — what customers say they're good at and where they frustrate
- [ ] **Recent news** (2 min) — funding, leadership change, new partnership, product launch
- [ ] **Job postings** (3 min) — hiring signals reveal where they're investing right now

## What to Never Do

Never go negative on a competitor in front of a client. The moment you start listing what the other
side does badly, you've made the client's evaluation harder — they start wondering what you're not
telling them about yourself. The strongest competitive responses don't name the competitor at all.

The version of this that goes wrong: over-prepared with competitor weaknesses, brought them all into
a client conversation, and the client left less confident rather than more. It signals that you're
threatened, not that you're the stronger option.

## How to Use

**Trigger:** "Run competitive analysis on [competitor type]"

**Inputs needed:**
- Competitor type (distribution-tier / AI-native / multi-cloud / analytics-first)
- Which service is relevant to this deal
- Client industry, company size, and use case — as much as you know

## What Good Output Looks Like

A tight brief under 300 words: a genuine assessment of the competitor's strengths so you walk in
without blind spots, your win conditions specific to this deal context (not generic), the framing
they've likely already planted with the client, and one clear 2–3 sentence response you could
deliver in the room without notes.

## Known Failure Modes

- **Speculative strengths presented as confirmed** — Claude doesn't know what the competitor said to
  this specific client; flag speculative bullets before using them
- **Generic output not tied to deal context** — if client context is vague, output will be vague;
  always specify industry and use case before triggering
- **Disparaging language in the response section** — if output goes negative, reject and re-run with
  explicit instruction to lead with your own strength only
- **Planted objection is too generic** — this is the most valuable section; push Claude to be
  specific about what this competitor type typically says in this deal scenario

---

## SKILL IMPLEMENTATION

```
You are a competitive intelligence analyst for a cloud and AI services company.

Competitor type: [DISTRIBUTION-TIER PARTNER / AI-NATIVE SPECIALIST / MULTI-CLOUD PARTNER / ANALYTICS-FIRST PARTNER]
Our service: [SERVICE RELEVANT TO THIS DEAL — e.g. cloud migration, managed services, AI/ML, cost optimisation]
Client context: [INDUSTRY / COMPANY SIZE / USE CASE / STAGE IN DEAL]

Produce:

1. WHERE THEY'RE STRONG (2–3 bullets)
Be honest. What do they genuinely do well that must be respected in this type of deal?
Do not dismiss them. Underestimating a competitor in front of a client costs more than acknowledging them.

2. WHERE WE WIN (2–3 bullets)
Where do we consistently outperform this competitor type in deals like this one?
Be specific to the client context provided — not generic claims.

3. WHAT THEY'VE LIKELY SAID (1–2 bullets)
Based on their positioning and this deal type, what framing or comparison have they probably
already planted with this client before this conversation?

4. OUR BEST RESPONSE (1 short paragraph)
The most effective 2–3 sentence response to their likely pitch.
Rules: specific to this deal context, not generic. Do not mention the competitor by name.
Lead with our strength. Do not reference their weakness.

Flag anything speculative with [ASSUMED]. Do not use disparaging language about the competitor.
```
