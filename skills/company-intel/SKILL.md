---
name: company-intel
description: "Moved to the research-intel skill (company mode): use research-intel when it is installed. Deep background research and competitive intelligence on a named company or organisation. Use this skill when the user asks for research, due diligence, a dossier, a deep dive, a brief or intelligence on a named subject, or names this skill. Triggers include: 'research [company]', 'due diligence on [company]', 'background on [company]', 'competitor analysis', 'who is [company]', 'prepare a dossier on [company]'. Also use when preparing for meetings with or pitches to a specific organisation. For an industry, market, sector, policy or regulation rather than one named entity, use topic-intel instead."
license: MIT
metadata:
  version: "1.6.2"
---

# Company Intelligence Research

**Moved.** This skill is now the company mode of `research-intel`. When `research-intel` is installed, use it instead. If not, tell the user once that this skill gets no more updates, then continue.

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

- `references/investigation-setup.md`: read at the start of every investigation for the dependency check, disambiguation, invocation menus, tier menu, web access layers and folder structure.
- `references/phase-playbook.md`: read before each research phase for the full step-by-step work.
- `references/ongoing-protocols.md`: read during and after the waves for progress reporting, the research log, confidence ratings, saturation and refresh.
- `references/australian-data-sources.md`: read at Phase 5 for Australian registers and source guidance.
- `references/osint-techniques.md`: read at Phase 8 for DNS, metadata, search operators, ad libraries and web archaeology.
- `references/analytical-frameworks.md`: read at Phase 11 for frameworks and templates.
- `references/investigative-methods.md`: read at Phase 5 and Phase 6 for due diligence and investigative techniques.
- `references/synthesis-outputs.md`: read at Phase 11 for synthesis templates and deliverable formats.
- `company-entity-modules.md`: read at Phase 0 Step 2 for the entity type modules.
- `company-expert-panels.md`: read at Phase 11 for the expert panel sets.
- `company-agent-dispatch.md`: read before Wave 1 when dispatching parallel agents.
- `references/INTELLIGENCE-STANDARDS.md`: read first at the start of every investigation.
- `references/web-access-layers.md`: read at investigation start for the four-layer web access protocol.
- `references/layer-4-playwright-protocol.md`: read when Layer 4 is triggered.

If a bundled reference under `references/` is missing, say so and carry on with this skill's own steps.

---

## Disambiguation

Confirm the subject is a named legal entity, not a broader topic. Read the Disambiguation section in `references/investigation-setup.md` for the classification table and the prompt. Use topic-intel for an industry, market, sector, policy or regulation rather than one named entity. If the user selects both, finish this investigation, then invoke topic-intel for sector context.

---

## Invocation Modes

Read the Invocation Modes section in `references/investigation-setup.md` for the menu. Use the menu when the user does not name a company. Skip the menu when the user names a company. Skipping the menu does not skip Phase 0. If the user names a company but gives no depth or KITs, finish every Phase 0 step, including the Company Scoping Document, before research begins.

## Investigation Tiers

Read the Investigation Tiers section in `references/investigation-setup.md` for the depth menu. Offer the depth after the company is identified. Ask the user to choose a depth before research starts. Use a depth named in the request without asking again. Quick Scan is the suggested depth.

---

## Web Access: Four-Layer Architecture

Read `references/investigation-setup.md` for the layer summary and the pre-investigation tool check. Read `references/web-access-layers.md` for the full protocol. Read `references/layer-4-playwright-protocol.md` before using Layer 4. Use Layer 4 only after the user says yes for the named source. Log a source as a gap on a no or when Playwright is not installed. Do not use Layer 4 on a source behind a login.

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
