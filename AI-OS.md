---
File: AI-OS.md
Type: Reference doc
Last updated: May 29, 2026
---

# My AI Operating System

## Philosophy
AI in my work is for accelerating the quality of my thinking — not 
replacing it. Specifically: first-pass research, reasoning through 
problems, finding gaps in my perspective, and stress-testing my ideas. 
AI is NOT for: financial inputs at work, legal review, or any output 
that goes to a client or CXO without my judgment applied first. 
Everything — including email rewrites — gets a proof check before it leaves me.

## Decision Framework
| Task Type | AI's Role | Model | Verify Before Use? |
|---|---|---|---|
| Pre-call research | First-pass synthesis — news, insights, tech stack, annual reports, public posts | Claude Sonnet 4.6 + Gemini 3.1 Pro + Web | Yes — cross-check key facts |
| Proposal draft | Error check + value proposition strengthening on a human-built draft | Claude Sonnet 4.6 | Yes — full review before sending |
| Product roadmap | Define features, architecture, UX flow; flag gaps I may have missed | Claude Sonnet 4.6 | Brief review before accepting suggestions |
| Client email cleanup | Reframe from scratch — concise, professional, CXO-appropriate structure | ChatGPT Plus | Spot check — no client names or deal terms in prompt |
| Competitive intel prep | Synthesis + positioning table | Claude Sonnet 4.6 + Gemini 3.1 Pro | Yes — validate against real deals |
| Executive briefing | Structure + language refinement | Claude Enterprise (Minfy) | Yes — read aloud before sending |
| Feature/product decisions | Options generation + critic layer stress-test | Claude → Gemini 3.1 Pro | Yes — critic layer mandatory |
| Personal finance strategy | Investment options against defined goals and budget | Claude Sonnet 4.6 + Gemini 3.1 Pro | Cross-validate both outputs; final judgment is mine |
| LinkedIn content | Draft post from brain dump in my established style | Claude Sonnet 4.6 | Iterate until acceptable, then fine-tune before posting |
| Financial or legal (work) | Never | — | — |

## My Tool Stack
- **Claude Sonnet 4.6 (Enterprise — Minfy license):** Primary tool for 
  all work tasks — drafting, synthesis, skill execution, agentic 
  workflows. Enterprise tier: no training on data, contractual 
  confidentiality.
- **Claude Pro (Personal — Consumer tier):** Personal queries, learning, 
  and non-work exploration only. Consumer tier — no work or client 
  content goes here.
- **Gemini 3.1 Pro (Web — Consumer tier):** Critic layer for 
  stress-testing Claude outputs. Consumer tier — no client or 
  commercial data.
- **Gemini API (GCP personal — API tier):** Powers user queries in my 
  Pre-Call Intel product. Not used for training by default. 
  Handles public-domain information only.
- **ChatGPT Plus (Consumer tier):** Email cleanup only. No client names, 
  deal terms, or commercial context in prompts.

## Model Comparison
*May 29, 2026 — same brief, both tools:*

- Structure: Claude used headers + red flags + sizing table — scannable 
  and decision-ready. Gemini used a 3-phase framework with a 
  qualification matrix — more thorough but slower to act on. 
  → Claude for speed, Gemini for depth when time allows.
- Assumptions made: Claude assumed high relationship trust from thin 
  context. Gemini assumed internal team alignment was needed — neither 
  assumption was in the brief. Both invented next steps. 
  → Check assumptions before acting on either output.
- Tone: Claude felt like a senior sales advisor — direct, risk-aware. 
  Gemini felt like a strategy consultant — structured but occasionally 
  generic (qualification matrix had no weighting between criteria). 
  → Claude for client-facing prep, Gemini for internal strategy framing.
- What each got right: Claude added red flags (no budget owner, vendor 
  already in mind) — Gemini missed this entirely. Gemini covered V2 
  roadmap questions and internal team alignment — both gaps in Claude. 
  → Run both on high-stakes briefs.
- Where each failed: Gemini's matrix was visually structured but 
  intellectually shallow — binary scoring, no guidance on which 
  criterion kills the deal. Claude's opportunity sizing offered no 
  method for arriving at numbers. → Neither replaces judgment.

## Verification Checklist
Before any AI-drafted content goes to a client or CXO:
- [ ] Factual claims about the client → cross-check LinkedIn / company site
- [ ] Numbers → verify against primary source
- [ ] Tone → read aloud before sending
- [ ] Claude assumed relationship trust from thin context → verify 
      relationship health before acting on any brief
- [ ] Claude invented assets I never mentioned → check any 
      "bring this document" advice against what actually exists

## Guardrails — What Never Goes In
- Client name + deal terms or pricing → enterprise tier only
- Internal margin, bid strategy, or AWS pricing data
- Colleague performance or HR-adjacent content
- Any work content into Claude Pro or ChatGPT Plus (consumer tier)
- Prospect proposal data outside enterprise Claude
- Personal passion project work on company enterprise license 
  without explicit policy clearance

## Currently Learning
May 2026 — Upskilling on AI infrastructure: RAG, LangGraph, LangChain, 
embeddings. Building automations and AI agents via n8n and Flowise. 
Goal: enterprise-grade agentic artifacts and a live public portfolio.
