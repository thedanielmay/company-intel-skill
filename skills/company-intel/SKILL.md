---
name: company-intel
description: "Deep background research and competitive intelligence on any company or organisation. Use this skill whenever the user wants to research a company, investigate a competitor, perform due diligence, understand an organisation's history and people, or prepare for a sales engagement. Triggers include: any mention of 'research [company]', 'look into [company]', 'background on [company]', 'due diligence', 'competitor analysis', 'who is [company]', or any request to understand a company's operations, financials, people, reputation, or digital presence. Also use when preparing for meetings with or pitches to a specific organisation. Even if the user just mentions wanting to know more about a company, invoke this skill."
license: MIT
metadata:
  version: "1.5.0"
---

# Company Intelligence Research

## Overview

A structured intelligence-gathering skill that performs deep, multi-source research on any company or organisation. It produces a dossier with provenance-tracked findings, a navigable folder structure and a professional PDF synthesis.

**Core principles:**
- Be exhaustive, systematic and transparent about findings and gaps.
- Every claim needs a source. Flag and interpret every gap.
- Triangulate across independent sources. Do not trust any single source.
- What a company does not say is often as revealing as what it says.
- The goal is actionable intelligence, not just information.

**Announce at start:** "Using the company-intel skill to conduct a deep background investigation."

## Dependency Check

Before doing anything else, run the dependency check in `references/investigation-setup.md`. It lists the four skills that work best with this one and the message to show when any are missing.

## Reference Files

Read each file when its trigger fires. Each file holds the detail that this body points to.

- `references/investigation-setup.md`: read at the start of every investigation for the dependency check, disambiguation, invocation menus, tiers, web access layers and folder structure.
- `references/phase-playbook.md`: read before each research phase for the full step-by-step work.
- `references/ongoing-protocols.md`: read during and after the waves for progress reporting, the research log, confidence ratings, saturation and refresh.
- `references/australian-data-sources.md`: read for the register of Australian data sources.
- `references/osint-techniques.md`: read for DNS, metadata, search operators, ad libraries and web archaeology.
- `references/analytical-frameworks.md`: read for analytical frameworks and templates.
- `references/investigative-methods.md`: read for investigative journalism and due diligence techniques.
- `references/synthesis-outputs.md`: read for synthesis templates and deliverable formats.
- `company-entity-modules.md`: read at Phase 0 Step 2 for the entity type modules.
- `company-expert-panels.md`: read at Phase 11 for the expert panel sets.
- `company-agent-dispatch.md`: read when dispatching parallel agents.
- `references/INTELLIGENCE-STANDARDS.md`: read first at the start of every investigation.
- `references/web-access-layers.md`: read for the four-layer web access architecture.
- `references/layer-4-playwright-protocol.md`: read when Layer 4 is triggered.

If a bundled reference under `references/` is missing, say so and carry on with this skill's own steps.

---

## Disambiguation

Confirm the subject is a named legal entity, not a broader topic. Read `references/investigation-setup.md` for the full classification table and the disambiguation prompt.

| Subject type | Use |
|---|---|
| Named company, charity, trust, government agency | company-intel, this skill |
| Industry, market or sector, not one company | topic-intel |
| Policy, regulation or framework | topic-intel |
| Ambiguous subject | Show the prompt in INTELLIGENCE-STANDARDS.md Section 14 |

If the user selects T, exit this skill and invoke topic-intel. If the user selects B, complete this investigation, then invoke topic-intel for sector context. In Phase 10, a full topic-intel study of the sector is often better than a lightweight market analysis here.

---

## Invocation Modes

**Menu-driven, the default:** use this menu when the user invokes the skill without naming a company.

```
COMPANY INTELLIGENCE RESEARCH
-----------------------------
1. New Investigation      - Start research on a company
2. Resume Investigation   - Continue an existing research dossier
3. Refresh Investigation  - Update an existing dossier with new data
4. Quick Scan             - Fast overview, 30 minutes equivalent
5. Revenue Discovery      - Find revenue opportunities for a social enterprise in crisis

Which would you like? (1-5)
```

**Direct invocation:** when the user names a company, skip the menu and go to Phase 0. Skipping the menu does not skip Phase 0. If depth and KITs are not specified, complete all Phase 0 steps, including the Company Scoping Document, before research begins.

## Investigation Tiers

Offer the investigation depth after the company is identified.

```
INVESTIGATION DEPTH
-------------------
1. Quick Scan          - Identity, website overview, recent news, key people. Fast.
2. Standard            - All of Quick Scan plus social, reviews, financials, digital footprint.
3. Full Investigation  - default. Everything: all sources, media downloads, deep analysis,
                         PDF synthesis, expert QA review.
4. Revenue Discovery   - Streamlined research plus deep revenue opportunity mapping.
                         For social enterprises and NFPs in financial crisis.

Which tier? (1-4, default: 3)
```

---

## Web Access: Four-Layer Architecture

Read `references/web-access-layers.md` for the full protocol.

- Layer 1, API first: ABR, ACNC, GrantConnect, AusTender, ASX. This is the fastest and most reliable layer.
- Layer 2, search as router: use WebSearch to find the exact URL, then fetch only that URL. Never crawl blind.
- Layer 3, scraping service: use when WebFetch returns blocked content and a service is configured.
- Layer 4, Playwright: opt in. Use it only after the user says yes for the named source.

**Opt-in rule:** if Layers 1 to 3 fail or do not apply, tell the user the source and the reason. Run Layer 4 only after the user says yes for that source. On a no, or when Playwright is not installed, log the source as a gap with the reason. Do not use Layer 4 on a source behind a login. Sources that often need Layer 4 include ACNC charity profile pages, Glassdoor, Facebook Ad Library, ASIC Connect search results, and any gov.au page with a CAPTCHA or session error.

**Wayback Machine:** web.archive.org is blocked. Use the CDX API:

```bash
curl "http://web.archive.org/cdx/search/cdx?url={domain}&output=json&limit=20"
```

**Pre-investigation tool check:** run once at investigation start. See INTELLIGENCE-STANDARDS.md Section 15 for the exact commands. Record the real results in `research-log.md`.

**Cascade failure prevention:** run no more than 3 or 4 WebFetch calls in parallel. Keep slow sources such as ACNC and gov.au in sequential calls.

---

## Research Phases

Run the phases in order. Wave parallelisation is described below. Read `references/phase-playbook.md` before starting each phase for the full steps.

### Phase 0: Intelligence Requirements Definition

Define the decision, the KITs, the end consumer and the time horizon. Confirm the Company Scoping Document with the user before any research. Classify the entity type at Step 2 using `company-entity-modules.md`. Complete the privacy checkpoint. The full steps and every template are in `references/phase-playbook.md`.

**STOP gate:** run no search, tool check or WebFetch call until the user confirms the Company Scoping Document.

**STOP gate:** do not begin research until the privacy checkpoint is complete and recorded.

### Phase 1: Identification and Entity Verification

Confirm the legal entity and separate it from similarly named companies. Map the corporate constellation through director searches. Create the folder structure. Save findings to `01-identification/`. Full steps are in `references/phase-playbook.md`.

### Phase 2: Website Analysis

Map and analyse the web presence: pages, messaging, products, team, technology stack and metadata. Download documents and inspect their metadata. Save to `02-website/`. Full steps are in `references/phase-playbook.md`.

### Phase 3: News and Media

Find articles, interviews, podcasts and videos, including negative coverage. Capture media and log items that cannot be downloaded in `outstanding-media.md`. Save to `03-news-media/`. Full steps are in `references/phase-playbook.md`.

### Phase 4: LinkedIn Deep Dive

Use only what is publicly visible without login through Layers 1 to 3, or what the user reads and pastes. Extract company page data, map the org chart, profile key people and read job postings. Flag anything that needs a login as a gap with the reason. LinkedIn is not a Layer 4 target. Save to `04-social-media/`. Full steps are in `references/phase-playbook.md`.

### Phase 4b: Other Social Media

Check Twitter/X, Facebook, Instagram, TikTok and YouTube. Record followers, frequency, themes and engagement for each platform. Save to `04-social-media/`. Full steps are in `references/phase-playbook.md`.

### Phase 5: Financial, Legal and Corporate Intelligence

Extract registry, financial, legal, ownership and compliance intelligence. Apply the data-currency warning to all registry data: note the last-lodged date and flag possible change. Cross-check every ASIC-derived structural finding against another source. Save to `05-financial-legal/`. Full steps are in `references/phase-playbook.md`.

### Phase 6: People Deep Profiling and Thread-Chasing

Profile Tier 1, 2 and 3 people. Follow career, board, education and investment threads. Frame behavioural observations as hypotheses, not findings. Cite at least two specific observations for every inference. Save to `06-people/`. Full steps are in `references/phase-playbook.md`.

### Phase 7: Reputation and Community Standing

Check reviews, Glassdoor, awards, forum discussions and media sentiment. For social enterprises, check certification status and beneficiary perception. Save to `07-reputation/`. Full steps are in `references/phase-playbook.md`.

### Phase 8: Digital Footprint and Technical Reconnaissance

Analyse DNS, domain history, website archaeology, source code, repositories, ad libraries and negative space. Read `references/osint-techniques.md` for the full techniques. Save to `08-digital-footprint/`. Full steps are in `references/phase-playbook.md`.

### Phase 9: Customers, Stakeholders and Beneficiaries

Identify who pays, who benefits and who influences. Map the stakeholder ecosystem. For social enterprises, assess the three markets and include beneficiary and funder analysis. Build introduction pathways for sales work. Save to `09-customers-stakeholders/`. Full steps are in `references/phase-playbook.md`.

### Phase 10: Industry and Market Context

Identify competitors, plot positioning and assess market dynamics. If the sector is a primary KIT, consider topic-intel for dedicated research. Reference any existing topic-intel dossier first. Save to `10-industry-market/`. Full steps are in `references/phase-playbook.md`.

### Phase 10b: Social Procurement and Revenue Opportunity Mapping

Use this phase in Revenue Discovery mode or for a social enterprise in crisis. Confirm the Revenue Discovery Scope with the user before research. Map capabilities to services, geography, peer revenue models, grants and quick wins. Save to `11-revenue-opportunities/`. Full steps are in `references/phase-playbook.md`.

### Phase 11: Synthesis and Expert Review

Turn research into actionable intelligence. Read `references/synthesis-outputs.md` for the templates and `company-expert-panels.md` for the QA process.

**Anti-hallucination protocol:**

- Produce `00-summary/synthesis-source-register.md` before writing any prose.
- Run the Fabrication Detection Pass after expert QA and write the `FABRICATION AUDIT` block.
- Verify every number against its source file before PDF generation.
- Watch for the company-intel fabrication risks listed in `references/phase-playbook.md`.

Also produce the KIT Answer Register, the triangulation matrix, the adversarial search and the confirmation bias check. Route the draft through the expert panels. Full steps are in `references/phase-playbook.md`.

**PDF generation gate:** generate the PDF only after all of these are true:

- The synthesis source register links every claim to a source.
- The Fabrication Detection Pass is complete with status CLEAR or ISSUES RESOLVED.
- No `[NUMERIC GAP - not sourced]` flags remain.
- All `[QA FLAG]` annotations are resolved.
- The triangulation matrix has no warning mark in the numeric verified column.

**PDF filename:** save the PDF at the root of the company folder, not inside `00-summary/`, named `full-synthesis-report-YYYY-MM-DD-HH:MM.pdf` using the completion date and time in 24-hour format. The working `synthesis.md` stays in `00-summary/` as the source of truth.

---

## Folder Structure

Use `_company-{slug}` for the dossier folder, with the company name lowercased and spaces replaced by hyphens. The final PDF sits at the folder root. Read `references/investigation-setup.md` for the full folder tree and naming rules. Every subfolder gets an INDEX.md with source, date, confidence rating and summary.

## Parallel Execution Strategy

Read `company-agent-dispatch.md` for the wave guide, agent briefings and timeout fallback.

- Wave 1: Phase 1 only. It must finish first.
- Wave 2: Phases 2, 3, 4 and the Phase 5 registry core, in parallel.
- Wave 2 threshold: if fewer than 2 independent sources confirm the entity, or a KIT has no findings, pause and report before Wave 3.
- Wave 3: Phases 4b, 6, 7, 8 and the Phase 5 deep dive, in parallel.
- Wave 4: Phases 9 and 10, in parallel.
- Wave 5: Phase 11 synthesis and expert QA.

## Operating Rules

Post the wave summary after every wave. The format is in INTELLIGENCE-STANDARDS.md Section 6. Append to `research-log.md` throughout. For registry entries, record the last-lodged date and the data-currency risk. Read `references/ongoing-protocols.md` for the full formats, the confidence ratings, the saturation rule and the refresh protocol.

---

## Key Principles

1. Decision-relevance over comprehensiveness. Orient everything toward the user's purpose.
2. Provenance on everything. Every fact cites its source with a confidence rating.
3. Independent sources matter. Two company press releases do not make two sources.
4. Gaps are intelligence. What is missing matters as much as what is found. Interpret every gap.
5. The Inversion Question. For key claims, ask what the evidence would look like if the opposite were true.
6. Forward-looking, not just backward-looking. Include scenarios, early warning indicators and So What implications.
7. Actionable outputs. The reader must know what to do, not just what to think.
8. Expert QA. Route synthesis through expert panels before finalising.
9. Be transparent about limitations. State assumptions, note stale data and flag access limits.
10. Ethical boundaries and access. Use public sources only. Do not misrepresent identity or access authenticated systems. Do not use stealth tools or session cookies. Respect each site's terms of service and robots rules. Comply with the Privacy Act and other applicable law.
11. Layer 4 is opt in. If Layers 1 to 3 fail, name the source and the reason to the user. Use Playwright only after the user says yes for that source. On a no, or when Playwright is not installed, log the source as a gap with the reason.
