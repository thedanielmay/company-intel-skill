# Company Agent Dispatch — Wave Parallelisation Guide

## Purpose

Guidance for parallelising company-intel investigation waves using agents. Agent dispatch converts the wave structure from aspirational parallelism to actual parallelism.

Agent dispatch is a performance optimisation, not a requirement. Sequential execution remains valid — all waves can be run in order without agents. Use this guide when investigation scope and available resources make parallel execution worthwhile.

**Reference:** See `superpowers:dispatching-parallel-agents` skill for Claude Code implementation details.

---

## Agent Briefing — Minimum Required Contents

Every agent dispatched from a company-intel investigation must receive all of the following in its briefing:

1. **Confirmed Company Scoping Document** — full text of `00-summary/company-scoping.md`
2. **Entity type module** — which entity module (STA/SME/ASX/PEQ/NFP/GOV/FOR) was classified in Phase 0
3. **KIT list with current status** — each KIT labelled: answered / partial / unanswered
4. **Research log excerpt** — sources accessed so far (prevents duplication)
5. **Specific task for this agent** — named source targets, what to look for, return format
6. **Tier constraint** — "This is a Tier [N] investigation. Do not use Layer [N+1] or above."
7. **Output instruction** — what to write back (see Handoff Format below)

Do not dispatch agents without the scoping document and research log.

---

## Handoff Format

Each agent writes a structured block to `research-log.md` when complete:

```markdown
## Agent task: [brief description] — [YYYY-MM-DD HH:MM]
Sources accessed: [N]
Layers used: [1/2/3/4]
KIT progress: KIT 1 [answered/partial/unanswered] | KIT 2 [...] | KIT 3 [...]
Key findings: [2-3 sentences — most significant findings]
Data-currency flags: [any ASIC, ACNC, or registry data where staleness may affect confidence]
Gaps logged: [N — reference inaccessible-sources.md for details]
New sources to follow up: [URLs or source names surfaced but not yet accessed]
```

---

## Wave-Level Parallelisation Notes

### Wave 1 — Foundation (do NOT parallelise)

Wave 1 confirms the entity, classifies entity type, establishes KITs, and produces the Company Scoping Document. All later agents need this document in their briefing. Do not dispatch agents before Wave 1 is complete.

### Wave 2 — Primary Research (parallelise by source cluster)

**Parallelisable tasks:**
- Website analysis and digital footprint core (Phase 2 + Phase 8 initial)
- News and media search (Phase 3)
- LinkedIn company page and founder profiles (Phase 4)
- Corporate registries core — ASIC + ABR + entity-type registries (Phase 5 core)

**Recommended agent type:** Explore (read-only source discovery)

**Per-agent brief structure:**
- **Agent A (Website + Digital):** "Analyse [company]'s website at [URL]. Map all pages, extract team, products, clients, messaging, job openings. Also perform DNS reconnaissance (A/MX/TXT records) and check crt.sh for subdomains. Record all findings with confidence ratings."
- **Agent B (News + Media):** "Search for all news, media coverage, podcasts, and video content mentioning [company name] and [founder names]. Date range: all available. Include: mainstream media, industry press, Trove (historical), SmartCompany, AFR. Log each source with date, publication, and summary."
- **Agent C (LinkedIn):** "Research [company]'s LinkedIn page and key people profiles. Extract: employee count and growth trend, team composition by function, leadership profiles (career history, education, tenure), job postings, recent posts and engagement. Note: LinkedIn notifications apply — see INTELLIGENCE-STANDARDS.md §16."
- **Agent D (Registries Core):** "Search ASIC, ABR, and [entity-type-specific registry] for [company]. Extract: full company extract, director history, document history (check for late lodgements), share structure, registered charges (PPSR). Flag any data with known staleness (see company-entity-modules.md data-currency note for this entity type)."

**Wave 2 minimum threshold gate:** If entity verification (Phase 1) returns fewer than 2 independent sources confirming the entity, or any KIT has zero substantive findings after Wave 2, pause and report to the user before Wave 3. Do not build synthesis on a thin evidence base.

### Wave 3 — Secondary Research (parallelise by phase)

**Parallelisable tasks:**
- People deep profiling — Tier 1 people (Phase 6)
- Reputation research — reviews, Glassdoor (Phase 7)
- Financial and legal deep dive — AustLII, grants, procurement (Phase 5 deep)
- Social media beyond LinkedIn (Phase 4b)
- Digital footprint depth — WHOIS, ad library, website archaeology (Phase 8 deep)

**Recommended agent type:** Explore

**Per-agent brief structure:**
- **Agent E (People Deep):** "Build Tier 1 profiles for [names]. For each: full career reconstruction across independent sources, board and advisory roles (ASIC cross-search), ASIC disqualified director check, AEC political donations, AustLII court records. Apply Thread-Chasing: career thread (all prior employers), board thread (all boards), education thread."
- **Agent F (Reputation):** "Research [company]'s reputation from: Google Reviews, Glassdoor (company and interview reviews), ProductReview, Whirlpool, Reddit. Also search for: '[company name] complaint', '[company name] lawsuit', '[company name] scam'. Record sentiment, recurring themes, and any specific incidents."
- **Agent G (Financial Deep):** "Search AustLII for all court and tribunal records involving [company name] and [director names]. Search GrantConnect and AusTender for full grant and contract history. Search Fair Work Commission. Search ACCC enforcement register. Extract all findings with source, date, and outcome."

### Wave 4 — Analysis (parallelise by framework)

**Parallelisable tasks:**
- Analytical frameworks (SWOT, Porter's Five Forces per `references/analytical-frameworks.md`)
- People profiles synthesis — Tier 2 and 3 (Phase 6)
- Customers and stakeholders mapping (Phase 9)
- Industry and market context (Phase 10)

**Recommended agent type:** General-purpose (analysis and writing)

**Per-agent brief structure:**
- **Agent H (Framework analysis):** "Apply [framework] to the following evidence set from the research log. Template: [paste from references/analytical-frameworks.md]. Evidence: [paste relevant research log sections]. Include a 'So What?' paragraph connecting the framework output to the stated purpose: [paste from company-scoping.md]."
- **Agent I (Industry/Market):** "Research the competitive and market context for [company]. Identify: direct and indirect competitors, competitive positioning, market dynamics, barriers to entry. Use topic-intel (Module MKT) if the sector itself is a primary KIT. Otherwise run Phase 10 scope only."

### Wave 5 — Synthesis and QA (partial parallelisation)

**Partially parallelisable:**
- Expert QA review — one agent per expert persona (Mode 3 pre-output QA)
- Deliverable file generation — one agent per output file

**Sequential gate:** Expert QA (Mode 3) must complete before PDF generation. All `[QA FLAG]` annotations must be resolved before invoking `document-skills:pdf`.

**Per-agent brief structure:**
- **Agent J (Expert QA):** "Review the attached synthesis draft as [Expert Name, role from company-expert-panels.md]. You are performing Mode 3 Pre-Output QA. Identify gaps, weak analysis, missing intelligence, or unsupported claims in your domain. Flag issues as [QA FLAG: Expert Name — description]. Do not soften findings — unresolved objections are valuable outputs."
- **Agent K (Deliverable generation):** "Write [specific deliverable] to [file path] using this template: [paste from references/synthesis-outputs.md]. Evidence base: [paste relevant synthesis sections]."

---

## Timeout and Fallback

- **Research agents (Waves 2-3):** Log incomplete tasks in research log: "Agent timed out — [task] incomplete." Continue without; note the gap in `inaccessible-sources.md`.
- **Analysis agents (Wave 4):** Run the framework sequentially in the main session if agent times out.
- **QA agents (Wave 5):** Do not skip QA. Run the expert review sequentially using the persona from `company-expert-panels.md` if the agent times out.

Sequential execution is always a valid fallback.

---

## Source Effort Caps by Tier

| Tier | Max layer | Playwright (Layer 4) | Scraping service (Layer 3) |
|---|---|---|---|
| Tier 1 — Quick Scan | Layer 2 | Never | Never |
| Tier 2 — Standard | Layer 3 | Never | Yes, if configured |
| Tier 3 — Full Investigation | Layer 4 | Yes | Yes |

Include the tier constraint in every agent briefing: "This is a Tier [N] investigation. Do not use Layer [N+1] or above."
