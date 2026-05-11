---
name: company-intel
description: "Deep background research and competitive intelligence on any company or organisation. Use this skill whenever the user wants to research a company, investigate a competitor, perform due diligence, understand an organisation's history and people, or prepare for a sales engagement. Triggers include: any mention of 'research [company]', 'look into [company]', 'background on [company]', 'due diligence', 'competitor analysis', 'who is [company]', or any request to understand a company's operations, financials, people, reputation, or digital presence. Also use when preparing for meetings with or pitches to a specific organisation. Even if the user just mentions wanting to know more about a company, invoke this skill."
---

# Company Intelligence Research

## Overview

A structured intelligence-gathering skill that performs deep, multi-source research on any company or organisation. Produces a comprehensive dossier with provenance-tracked findings, organised into a navigable folder structure with a professional PDF synthesis.

**Core principles:**
- Be exhaustive, systematic, and transparent about what you found and what you couldn't find
- Every claim needs a source. Every gap needs to be flagged and interpreted
- Triangulate across independent sources — don't trust any single source
- What a company doesn't say is often as revealing as what it does say
- The goal is actionable intelligence, not just information

**Announce at start:** "Using the company-intel skill to conduct a deep background investigation."

## Dependency Check

Before doing anything else, check whether the following skills appear in the available skill list for this session:

- `expert-panel`
- `document-skills:pdf`
- `data-visualization`
- `topic-intel`

If ANY are missing, say:

> "company-intel works best with its full skill set. The following skills are missing from this session:
> [list the missing ones]
>
> Install them using either method below, then restart your session:
>
> **`expert-panel`**
> - `npx skills add thedanielmay/expert-panel-skill`
> - `/plugin install expert-panel@thedanielmay`
>
> **`document-skills:pdf`**
> - `npx skills add anthropics/claude-plugins-official@document-skills`
>
> **`data-visualization`**
> - `npx skills add anthropics/claude-plugins-official@data-visualization`
>
> **`topic-intel`**
> - `npx skills add thedanielmay/topic-intel-skill`
> - `/plugin install topic-intel@thedanielmay`
>
> Or type **'continue anyway'** to proceed — steps that need missing skills will be skipped."

If the user types 'continue anyway', note which skills are unavailable and proceed. When a missing skill would normally be invoked, skip that step and note it inline: "(skipped — `topic-intel` not available)".

If all skills are present, proceed silently without mentioning the check.

---

**Reference files:** This skill uses detailed reference documents. Read them when each phase requires their specific guidance:
- `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` — **Read this first at the start of every investigation.** Universal standards: STOP gate, scoping document, KIT Answer Register, confidence ratings, saturation rule, wave thresholds, progress reporting, synthesis sequence, universal deliverables, disambiguation routing, tool check, ethical boundaries.
- `~/.claude/skills/shared/references/web-access-layers.md` — Four-layer web access architecture.
- `~/.claude/skills/shared/references/layer-4-playwright-protocol.md` — Complete Layer 4 Playwright protocol. Read when Layer 4 is triggered.
- `references/australian-data-sources.md` — Comprehensive register of Australian data sources.
- `references/osint-techniques.md` — Technical OSINT techniques (DNS, metadata, search operators, ad libraries, web archaeology).
- `references/analytical-frameworks.md` — All analytical frameworks and templates.
- `references/investigative-methods.md` — Investigative journalism and due diligence techniques.
- `references/synthesis-outputs.md` — All synthesis output templates and deliverable formats.
- `company-entity-modules.md` — Entity-type module definitions (STA/SME/ASX/PEQ/NFP/GOV/FOR). Read at Phase 0 Step 2.
- `company-expert-panels.md` — Entity-type expert panel sets with 3 integration modes. Read at Phase 11.
- `company-agent-dispatch.md` — Wave parallelisation guide with agent briefing templates. Read when dispatching parallel agents.

---

## Disambiguation: company-intel vs topic-intel

Before starting, confirm the subject is a named legal entity, not a broader topic. See `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` Section 14 for the full classification table and disambiguation prompt.

| Subject type | Use |
|---|---|
| Named company, charity, trust, government agency | company-intel (this skill) |
| Industry, market, or sector (not one specific company) | topic-intel |
| Policy, regulation, or framework | topic-intel |
| Ambiguous — company mentioned but context suggests market/sector interest | Show disambiguation prompt (INTELLIGENCE-STANDARDS.md §14) |

**If user selects T:** Exit this skill. Invoke topic-intel instead.
**If user selects B:** Complete this company-intel investigation, then invoke topic-intel for the sector context. When running Phase 10 (Industry & Market), note that a full topic-intel investigation of the sector may be warranted rather than a lightweight market analysis inside this skill.

---

## Invocation Modes

**Menu-driven** (default): When the user invokes the skill without specifying a company:

```
COMPANY INTELLIGENCE RESEARCH
─────────────────────────────
1. New Investigation      — Start research on a company
2. Resume Investigation   — Continue an existing research dossier
3. Refresh Investigation  — Update an existing dossier with new data
4. Quick Scan             — Fast overview (30-min equivalent)
5. Revenue Discovery      — Find revenue opportunities for a social enterprise in crisis

Which would you like? (1-5)
```

**Direct invocation**: When the user specifies a company name, skip the menu and go directly to Phase 0. **Skipping the menu does not skip Phase 0.** If the company is named but investigation depth and KITs are not specified, still complete all Phase 0 steps — including the Company Scoping Document — before any research begins.

## Investigation Tiers

After identifying the company, offer the investigation depth:

```
INVESTIGATION DEPTH
───────────────────
1. Quick Scan          — Identity, website overview, recent news, key people. Fast.
2. Standard            — All of Quick Scan + social, reviews, financials, digital footprint.
3. Full Investigation  — (default) Everything. All sources, media downloads, deep analysis,
                          PDF synthesis, expert QA review.
4. Revenue Discovery   — Streamlined research + deep revenue opportunity mapping.
                          For social enterprises and NFPs in financial crisis.

Which tier? (1-4, default: 3)
```

## Web Access — Four-Layer Architecture

Read `~/.claude/skills/shared/references/web-access-layers.md` for the full four-layer protocol (API -> search-as-router -> scraping service -> Playwright).

**Summary:**
- **Layer 1 — API-first:** ABR, ACNC (data.gov.au), GrantConnect, AusTender, ASX. Fastest and most reliable.
- **Layer 2 — Search as router:** Use WebSearch to find the exact URL, then fetch only that URL. Never crawl blind.
- **Layer 3 — Scraping service:** When WebFetch returns blocked/empty content and a service is configured.
- **Layer 4 — Playwright:** Universal fallback. Always attempt before declaring a source inaccessible.

**Universal fallback rule:** If Layers 1-3 fail or are inapplicable, ALWAYS attempt Layer 4 before logging a gap. Known company-intel sources requiring Layer 4: ACNC charity profile pages, Glassdoor, Facebook Ad Library, ASIC Connect search results, LinkedIn company and profile pages, any gov.au page returning a CAPTCHA or session error.

**Wayback Machine:** web.archive.org is blocked. Use the CDX API:
```bash
curl "http://web.archive.org/cdx/search/cdx?url={domain}&output=json&limit=20"
```

**Pre-investigation tool check:** Run once at investigation start. See `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` Section 15 for the exact commands. Record actual results in `research-log.md`.

**Cascade failure prevention:** Never run more than 3-4 WebFetch calls in parallel. Put known-slow sources (ACNC website, gov.au) in sequential calls, not batches.

---

## Phase 0: Intelligence Requirements Definition

**Goal:** Define what decision this intelligence supports, so every subsequent phase is focused and the deliverable is relevant.

This is the single most important phase. Skip it and you produce a data dump. Do it well and you produce actionable intelligence.

### Process

Ask the user (if not already clear from context):

```
INTELLIGENCE REQUIREMENTS
─────────────────────────
1. What is your purpose? (choose one)
   a. Competitive analysis     — understand a competitor
   b. Sales / BD preparation   — prepare to sell to or partner with
   c. Due diligence            — evaluate for acquisition or investment
   d. Partnership evaluation   — assess a potential partner
   e. Social enterprise review — assess a mission-driven organisation
   f. Revenue discovery        — find revenue opportunities (social enterprise/NFP)
   g. General background       — broad understanding
   h. Integrity investigation  — check for problems or red flags

2. What are your Key Intelligence Topics (KITs)?
   (The 2-5 questions you most need answered)

3. Who is the end consumer of this intelligence?
   (You personally? A board? A sales team? An investment committee?)

4. What is the time horizon?
   (Immediate decision / ongoing monitoring / strategic planning)
```

**The purpose drives everything.** It determines:
- Which phases get the deepest treatment
- Which expert reviewers are selected for QA (see `references/expert-panels.md`)
- Which synthesis output templates are used (see `references/synthesis-outputs.md`)
- What the executive summary leads with

**Save to:** `00-summary/intelligence-requirements.md`

### Step 5: Company Scoping Document

Before any research begins, confirm this document with the user:

```
COMPANY SCOPING DOCUMENT
────────────────────────
Company:       [legal name as confirmed in Phase 0]
Trading as:    [if different]
Purpose:       [letter from 1a–1h]
Depth tier:    [1–4 — name]
Output:        [what will be produced]

Key Intelligence Topics:
  1. [KIT 1]
  2. [KIT 2]
  [additional KITs]

End consumer:  [who receives this intelligence]
Time horizon:  [immediate / ongoing / strategic]

Scope inclusions:
  [Specific subsidiaries, geographies, time ranges, or aspects to prioritise]

Scope exclusions:
  [What is explicitly out of scope — prevents drift]

Output location:
  _company-{slug}/

────────────────────────
Does this capture what you need? (yes / adjust scope / change KITs)
```

**Research does not begin until the user confirms this document.**

**STOP — do not proceed to Phase 1 or run any searches, WebFetch calls, or tool checks until the user has confirmed the Company Scoping Document. Presenting the questions and proceeding immediately is the single most common failure mode. Resist it.**

Save to: `_company-{slug}/00-summary/company-scoping.md`

### Step 6: Entity Type Classification

After the Scoping Document is confirmed, classify the target entity before KIT elicitation. Read `company-entity-modules.md` and select the matching entity type:

```
ENTITY TYPE
───────────
  STA — Startup / early-stage
  SME — Private SME
  ASX — ASX-listed company
  PEQ — PE-backed or VC-backed (mature)
  NFP — NFP, charity, or social enterprise
  GOV — Government agency or statutory body
  FOR — Foreign subsidiary or branch

Entity type: [code]
```

Once classified, load the matching module from `company-entity-modules.md` for:
- Default KIT suggestions (propose to user if KITs not specified)
- Source priority order for this entity type
- Phase emphasis (which phases get deepest treatment)
- Data-currency warning applicable to this entity type
- Output variant

Save the classified entity type to `00-summary/company-scoping.md`.

### Step 7: Privacy and Compliance Checkpoint

Before any research begins, answer these questions and record answers in `00-summary/company-scoping.md`:

```
PRIVACY AND COMPLIANCE CHECKPOINT
──────────────────────────────────
1. Does this investigation target or likely surface personal information
   about identifiable individuals (directors, beneficial owners, employees)?
   [yes / no / likely]

2. What is the legitimate purpose for collecting this information?
   [business decision / due diligence / competitive analysis / other]

3. Are there any individuals whose data will be collected who are not
   public figures and whose private life might be surfaced inadvertently?
   [yes / no — if yes, scope exclusions must address this]

4. Will Playwright (Layer 4) be used? If yes, note that:
   - Research leaves traces visible in website analytics
   - LinkedIn notifies profile owners when viewed
   - Some platforms prohibit scraping in their Terms of Service
   - Spread research across sessions for sensitive investigations
```

**What this checkpoint does NOT replace:** Legal advice for high-stakes investigations. For due diligence involving personal data at scale, consult a privacy lawyer before proceeding. The Privacy Act 1988 (Cth) and the APPs apply when personal information about identifiable individuals is collected for commercial purposes.

**STOP:** Do not begin research until this checkpoint is completed and recorded.

---

## Phase 1: Identification & Entity Verification

**Goal:** Confirm the exact legal entity, distinguish from similarly named companies, and establish the corporate structure.

### Process

1. Search ABN Lookup, ASIC, ACNC (for Australian entities). For international entities, use equivalent national registers.
2. Search for the company website.
3. Present confirmation to the user:
   ```
   COMPANY IDENTIFICATION
   ──────────────────────
   Legal name:      [name]
   Trading as:      [if different]
   ABN/ACN:         [number]
   Entity type:     [Pty Ltd / Ltd / Charity / Trust / etc.]
   Registered:      [date]
   Status:          [Active / Cancelled / etc.]
   Jurisdiction:    [State, Country]
   Website:         [URL]
   Industry:        [sector]

   Is this the right entity? (yes/no)
   ```
4. If ambiguous, present all candidates and let the user choose.
5. **Related Entity Discovery:** For every director identified, search ASIC for all other companies where they hold/have held directorships. Map the corporate constellation. Note shared addresses, auditors, company secretaries. See `references/investigative-methods.md` Section 2.
6. Create the research folder structure (see Folder Structure below).
7. Save identification data to `01-identification/`.

**Exit criteria:** Entity confirmed. Corporate constellation mapped. Folder structure created.

---

## Phase 2: Website Analysis

**Goal:** Map and analyse the company's entire web presence.

1. **Complexity assessment** — fetch homepage and sitemap, estimate pages, platform, crawl effort. Present to user.
2. **Website mapping** — sitemap from navigation/footer/discovered pages. Categorise pages.
3. **Deep page analysis** — messaging, products/services, team, client logos, testimonials, case studies, partners, impact claims, certifications, job openings, blog themes, contact details.
4. **Technical analysis** — tech stack from source (CMS, frameworks, analytics, marketing tools). Check structured data. Assess UX quality.
5. **Document and image metadata** — download all PDFs/docs. Extract metadata (author, creator, dates, internal file paths). Reverse image search team photos. See `references/osint-techniques.md` Sections 6-7.

**Save to:** `02-website/` | **Quick Scan:** Homepage + About + key pages only.

---

## Phase 3: News & Media

**Goal:** Find everything published about this company — articles, interviews, podcasts, videos.

1. **Broad news search** — company name, founder names, key people. Go back as far as possible. Use date-bounded searches to ensure coverage across years. See `references/osint-techniques.md` Section 9 for Google Dork techniques.
2. **Australian-specific sources** — search Trove (historical newspapers), Parliamentary Hansard, SmartCompany, AFR, Pro Bono Australia (for NFPs). See `references/australian-data-sources.md`.
3. **Interview and podcast hunting** — YouTube, podcast directories, conference talks, panel appearances.
4. **Media capture** — download media files where possible. Log items that cannot be downloaded to `outstanding-media.md` with URL, platform, date, reason, manual download instructions.
5. **Negative coverage search** — specifically search for: complaint, lawsuit, scam, fraud, dispute, failure, scandal, investigation. Check Whirlpool, ProductReview, Reddit.
6. **Media analysis** — themes over time, public claims, self-presentation, interviewer questions, contradictions, controversies.

**Save to:** `03-news-media/` with naming: `YYYY-MM-DD_source_title.md` | **Quick Scan:** Last 12 months only, no downloads.

---

## Phase 4: LinkedIn Deep Dive

**Goal:** Extract maximum intelligence from LinkedIn — the richest public source for people, structure, and trajectory.

1. **Company page** — employee count, growth trend, specialties, locations, posts, engagement, "People Also Viewed" peers.
2. **Employee mapping** — reconstruct org chart from titles. Map leadership, middle management, specialists. Team size by function. Former employee exit destinations. New hire entry sources. Tenure distribution.
3. **Key people's profiles** — career history, education, skills, recommendations network, recent activity, connections of note, board/advisory roles.
4. **Job postings** — current openings, skills sought, salary ranges, remote/hybrid, growth signals.
5. **Network intelligence** — who engages with their posts, thought leadership positioning.

**Note:** LinkedIn data accessibility varies. Flag which findings depend on publicly accessible data vs data that would require Sales Navigator.

**Save to:** `04-social-media/linkedin-*` files | **Quick Scan:** Company page + founder profiles only.

## Phase 4b: Other Social Media

Twitter/X, Facebook, Instagram, TikTok, YouTube channel. Per-platform: followers, frequency, themes, engagement. Cross-platform consistency analysis.

**Save to:** `04-social-media/` | **Quick Scan:** Skip.

---

## Phase 5: Financial, Legal & Corporate Intelligence

**Goal:** Extract all financial, regulatory, legal, and corporate structure intelligence.

This is a deep phase. Read `references/australian-data-sources.md` for the full register of sources and `references/investigative-methods.md` for forensic techniques.

### Core Searches
1. **Corporate registrations** — ASIC (full extract including historical document history), ABN Lookup (including Historical Details tab), ACNC for charities, ASX for listed companies.

**Data-currency warning (applies to all registry sources):** Official registry data (ASIC, ACNC, ABR) reflects filings as of lodgement date. Corporate restructures, director changes, and address updates may lag weeks to months. Apply ★★★ confidence for official status, but always note the last-lodged date and flag that the structure may not reflect the current position. The entity-type module (loaded in Phase 0) specifies the typical lag for this entity type. Cross-reference any ASIC-derived structural finding against at least one other source (LinkedIn, media, company website) to check for signs of change.

2. **Historical corporate structure** — Map name changes, director rotations, address shifts, share transfers over time ("Shedding Skin" technique). See `references/investigative-methods.md` Section 1.
3. **Financial data** — ACNC financials, annual reports, ASX filings, government grant data (GrantConnect, state databases), tender history (AusTender + state portals).
4. **Financial analysis** — Read `references/analytical-frameworks.md` for: revenue decomposition, common-size financial statements, unit economics estimation, normalised earnings, working capital analysis, revenue sustainability scorecard.
5. **Legal and compliance** — AustLII (primary, all jurisdictions), Federal Court, state tribunals, Fair Work Commission, ACCC enforcement register, PPSR, ASIC Banned & Disqualified Register. See `references/investigative-methods.md` Section 7.
6. **Beneficial ownership tracing** — Follow corporate chains, trust structures, nominee arrangements. See `references/investigative-methods.md` Section 3.
7. **Regulatory registers** — Industry-specific: AFSL, NDIS Commission, Aged Care Commission, EPA, WorkSafe, Modern Slavery Register, OAIC, as applicable.
8. **Property searches** — State land title offices for company and director property holdings. See `references/investigative-methods.md` Section 4.

### Social Enterprise Financial Deep Dive (if applicable)
For social enterprises/NFPs, additionally assess: earned income ratio, revenue concentration risk (top 1/3/5 funders), grant cliff risk, reserves ratio (months), workforce cost ratio, group structure complexity, DGR status. See `references/analytical-frameworks.md` Social Enterprise Frameworks section.

**Save to:** `05-financial-legal/` | **Quick Scan:** ABN/ASIC check only. **Standard:** Registration + financials, skip legal deep dive.

---

## Phase 6: People Deep Profiling & Thread-Chasing

**Goal:** Build comprehensive profiles of key individuals and follow the threads of their networks.

### Tier System
- **Tier 1** (founders, CEO, key leaders): Full career reconstruction, decision-style analysis, network mapping, behavioural indicators
- **Tier 2** (board, senior management, departing staff): Career history, role analysis, network connections
- **Tier 3** (notable staff, advisors): Brief profiles with role and background

### Thread-Chasing Methodology
For each Tier 1 person, follow connections 2-3 degrees out:
1. **Career thread** — every previous employer. What happened to those organisations? Who else worked there?
2. **Board thread** — every board position. Who else sits on those boards? What do those organisations do?
3. **Education thread** — alma mater, notable alumni connections, academic publications.
4. **Investment/advisory thread** — what else have they invested in or advised?

### Background Checks
- ASIC disqualified director search, court/tribunal records (AustLII), professional register checks, political donation searches (AEC transparency register), lobbyist register.
- See `references/investigative-methods.md` Section 12 for exit pattern analysis and recommender network technique.

### Behavioural and Communication Analysis
Frame all behavioural observations as hypotheses, not findings. Every inference must cite at least two specific observations. Use language: "Observable pattern suggests..." not "Their motivation is..."

**Save to:** `06-people/` with subfolders per person | **Quick Scan:** Founders only, basic profiles.

---

## Phase 7: Reputation & Community Standing

Google Reviews, Glassdoor, industry awards, community mentions, forum discussions, media sentiment analysis. For social enterprises: Social Traders certification status, B Corp score breakdown, beneficiary community perception.

**Save to:** `07-reputation/`

---

## Phase 8: Digital Footprint & Technical Reconnaissance

**Goal:** Analyse the company's involuntary digital footprint — what their infrastructure and metadata reveal.

This phase has significantly more depth than the others. Read `references/osint-techniques.md` for full techniques.

### Core Analysis
1. **DNS reconnaissance** — A/MX/TXT/CNAME/NS records. SPF/DKIM/DMARC analysis revealing email infrastructure and third-party services. Subdomain enumeration via crt.sh certificate transparency.
2. **Domain intelligence** — WHOIS data, historical WHOIS, reverse WHOIS (all domains by same registrant), domain age.
3. **Website archaeology** — Wayback Machine CDX API for full URL inventory. Deleted page recovery. robots.txt history. Snapshot diffing of key pages over time.
4. **Source code analysis** — Google Analytics/GTM ID reverse lookup, tracking pixels, meta tags, developer comments, robots.txt blocked paths.
5. **Code repositories** — GitHub/GitLab/Bitbucket search for company and employee accounts.
6. **Advertising intelligence** — Google Ads Transparency Center, Meta Ad Library, LinkedIn Ad Library.
7. **Negative space analysis** — structured checklist of what's missing and what that means.

**Save to:** `08-digital-footprint/` | **Quick Scan:** Skip. **Standard:** Basic tech stack only.

---

## Phase 9: Customers, Stakeholders & Beneficiaries

**Goal:** Identify who pays, who benefits, and who influences.

### Customer Identification
Search for clients via: website case studies/logos, news articles, government procurement records (AusTender, state portals), annual reports/ACNC filings, social media tags, industry award submissions, partner announcements.

### Stakeholder Ecosystem Map
Map all stakeholders: customers, funders, partners, suppliers, regulators, community groups, industry bodies, beneficiaries (for social enterprises — distinct from customers).

### Social Enterprise Three-Market Model (if applicable)
- **Impact Market** — beneficiaries and their communities
- **Revenue Market** — paying customers, procurement officers, grant-makers
- **Talent Market** — staff, volunteers, board members

Assess health of each market independently. Include beneficiary analysis and funder motivation analysis. See `references/analytical-frameworks.md`.

### Introduction Pathways (for sales/BD purposes)
Cross-reference target's people network against potential mutual connections. Construct referral chains. Identify shared communities, events, associations.

**Save to:** `09-customers-stakeholders/`

---

## Phase 10: Industry & Market Context

**Goal:** Place the company in its competitive and market context.

**Note:** If the sector itself is a primary KIT — not just background context for this specific company — consider invoking the topic-intel skill (Module MKT or POL) for dedicated sector research. Use topic-intel when substantial market sizing, regulatory landscape, or ecosystem analysis is needed. Reference any existing topic-intel dossier for this sector before running fresh Phase 10 research.

1. **Competitor identification** — direct, indirect, and emerging competitors.
2. **Competitive positioning map** — plot target and competitors on two most relevant axes.
3. **Market dynamics** — size, growth, trends, regulatory environment, barriers to entry.
4. **Competitive benchmarking matrix** — structured comparison across: product breadth, pricing, geographic reach, customer focus, technology, brand strength, talent, financial resources, growth trajectory.
5. **Win/loss intelligence** — from public tender results, media, reviews.
6. **Talent flow analysis** — where employees go when they leave, where new hires come from (connect to Phase 4 LinkedIn data).

**Save to:** `10-industry-market/`

---

## Phase 10b: Social Procurement & Revenue Opportunity Mapping (Revenue Discovery Mode only)

Triggered when investigation purpose is revenue discovery or the target is a social enterprise in crisis.

**Before beginning Revenue Discovery research, confirm the following with the user:**

```
REVENUE DISCOVERY SCOPE
───────────────────────
Enterprise:          [legal name]
Crisis context:      [brief — what the immediate revenue gap is]
Capability base:     [confirmed current capabilities]
Time horizons:       [0–90 days / 6–12 months / 12+ months — which to prioritise]
Opportunity types:   [social procurement / grants / earned income / partnerships — which to prioritise]
Output consumer:     [board / CEO / advisor / funder]

Does this capture the scope? (yes / adjust)
```

Research does not begin until confirmed.

1. **Service-market matching** — current capabilities → adjacent services → which are in demand through social procurement.
2. **Geographic opportunity mapping** — local governments with social procurement policies, state department procurement, local corporates with RAP/ESG commitments, upcoming infrastructure projects.
3. **Peer enterprise revenue model analysis** — 3-5 similar SEs, their revenue models via ACNC, what streams the target lacks.
4. **Grant and philanthropic pipeline** — GrantConnect, Philanthropy Australia, state programs, Community Foundations.
5. **Quick win identification** — 0-90 day, 6-12 month, 12+ month revenue opportunities.
6. **Crisis stabilisation intelligence** — emergency grants, sector intermediary support, merger/partnership/auspice opportunities, unused asset capacity.

**Save to:** `11-revenue-opportunities/`

---

## Phase 11: Synthesis & Expert Review

**Goal:** Transform research into actionable intelligence. This is where information becomes insight.

**Anti-hallucination protocol:** This phase uses three enforcement mechanisms from `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md`:
- **Step 0 (Cite-Before-You-Write):** Produce `00-summary/synthesis-source-register.md` before writing any prose
- **Step 6b (Fabrication Detection Pass):** Apply the Fabrication Red Flags checklist (Section 17) after Expert QA
- **Step 7b (Numeric Quarantine):** Verify every number against its source file before PDF generation

Read Section 8 of INTELLIGENCE-STANDARDS.md for the full protocol, Section 7 for the Numeric Verification Protocol, and Section 17 for the Fabrication Red Flags checklist.

Read `references/synthesis-outputs.md` for all templates and `references/expert-panels.md` for the QA process.

### Company-Intel Specific Fabrication Risks

The following hallucination patterns are particularly common in entity research. Watch for them during the Fabrication Detection Pass:

- **Invented financial metrics** — revenue, EBITDA, employee count, or market share stated without a traceable source. ASIC does not require private companies to disclose financials; absence of a source means absence of data, not a licence to estimate.
- **Corporate structure drift** — a director, subsidiary, or address stated from memory of Phase 1 that does not match the ASIC extract in `05-financial-legal/`. Always re-check the extract, not memory.
- **Behaviour attributed as motivation** — "The company does X because Y" stated as fact without a source attributing the motivation. Observable patterns only — never inferred intent as stated fact.
- **Stale registry data asserted as current** — any ASIC or ACNC structure stated without noting the last-lodged date. All registry-derived structure claims must carry: "as of [last-lodged date]."
- **People profile contamination** — claims about Person A migrating to Person B's profile when multiple Tier 1 people are researched in parallel. Cross-check every proper noun against the specific profile file in `06-people/`.

### Step 1: KIT Answer Register

Before proceeding to frameworks or deliverables, produce a structured answer for each KIT from Phase 0:

```
KIT [N]: [question]
Answer:      [direct answer — 2–5 sentences. Lead with the answer, not the caveats.]
Confidence:  [★★★ / ★★ / ★]
Key sources: [2–3 most authoritative sources used]
Gaps:        [what would improve confidence if found]
```

If KIT answers point in contradictory directions, surface this tension explicitly in the Executive Summary. Do not resolve it artificially.

Save to: `00-summary/kit-answers.md`

### Step 2: Triangulation & Verification
- Build the triangulation matrix for all key findings (see template in `references/synthesis-outputs.md` Section 17)
- Verify source independence — mark each source as Primary / Secondary Independent / Secondary Dependent
- Apply Analysis of Competing Hypotheses (ACH) for any contradictory findings (see `references/analytical-frameworks.md`)
- Run the Narrative Consistency Audit (see `references/investigative-methods.md` Section 11)
- Apply the "Inversion Question" to the 3 strongest positive claims

### Step 3: Analytical Frameworks
Select frameworks based on investigation purpose. Read `references/analytical-frameworks.md` for templates.

**Always apply:**
- SWOT (informed by all research)
- Relevant industry framework (Porter's Five Forces or Value Chain)

**Apply based on purpose:**
- Financial frameworks (revenue decomposition, sustainability scorecard) — for due diligence, investment
- Sales frameworks (MEDDPICC, buying signals, DMU mapping) — for sales/BD
- Social enterprise frameworks (typology, mission drift, three-market model) — for SE targets
- Scenario analysis (bull/base/bear) — for strategic decisions

Every framework output MUST include a "So What?" paragraph connecting it to the user's stated purpose.

### Step 4: Adversarial Search

Before the Confirmation Bias Check, run an explicit adversarial search to surface evidence the KIT-driven investigation may have missed. KITs are a confirmation architecture — they direct research toward known risks. This step directs research toward unknown risks.

For each KIT, run one counter-hypothesis search:

```
KIT [N]: [the question]
Counter-hypothesis: [the opposite of what the investigation currently shows]
Adversarial search queries:
  - "[company name]" "[counter-hypothesis term]"
  - "[director name]" "[failure/dispute/complaint/enforcement]"
  - "[company name]" -site:[company domain] "[negative signal term]"
Sources to check specifically:
  - AustLII (court records, tribunal decisions)
  - Whirlpool, ProductReview, Reddit (community sentiment)
  - Fair Work Commission decisions
  - ACCC enforcement register
  - Glassdoor (if not already accessed)
```

Document any findings in a new file: `00-summary/adversarial-findings.md`.

If the adversarial search returns findings that materially contradict the KIT answers, surface this tension explicitly in the Executive Summary. Do not resolve it artificially.

### Step 5: Confirmation Bias Check
Before finalising, apply the Devil's Advocate check:
- What evidence contradicts the central narrative?
- Document at least 3 findings that cut against the primary thesis
- Have competing hypotheses been considered for ambiguous findings?

### Step 6: Expert Panel Review

Read `company-expert-panels.md` and select the expert set matching the entity type classified in Phase 0.

**Mode 1 — Synthesis Reviewer (always invoke for Full Investigations):**
1. Select 2-3 experts most relevant to the primary KITs
2. For each expert, apply their key questions to the draft synthesis
3. Flag gaps as `[QA FLAG: Expert Name — issue]`
4. Resolve all `[QA FLAG]` annotations before deliverable generation

**Mode 3 — Pre-Output QA (invoke before PDF generation):**
Route the complete dossier through all three experts for the entity type. Any unresolved `[QA FLAG]` blocks the PDF generation step.

**On-demand adversarial review:** If the user requests a full expert panel challenge, invoke the `expert-panel` skill using the personas from `company-expert-panels.md` as the starting point.

### Step 7: Build Deliverables
Generate outputs based on purpose (all templates in `references/synthesis-outputs.md`):

**Always produce:**
1. RAG Dashboard (one-page traffic-light summary — always the first page)
2. Critical Findings (5-7 most decision-relevant findings)
3. Executive Summary (purpose-oriented)
4. Assumptions and Limitations
5. Information Gaps (with interpretation — not just listed)
6. Monitoring Plan (Google Alerts, filing dates, trigger events, refresh cadence)

**Produce based on purpose:**
- Engagement Playbook (for sales/BD) — approach angle, conversation framework, stakeholder sequence, landmine map
- Competitive Battle Cards (if competitors identified)
- Buying Signal Register (for sales/BD)
- Timing Intelligence (for sales/BD)
- Revenue Discovery outputs (for social enterprise crisis)
- Purpose-specific Executive Briefing (1-2 page brief per `references/synthesis-outputs.md` Section 4)

**PDF generation gate:** Before generating the PDF, confirm ALL of the following:
- [ ] `00-summary/synthesis-source-register.md` is complete — every synthesis claim has a source entry
- [ ] Fabrication Detection Pass complete — `FABRICATION AUDIT` block written in synthesis.md with status CLEAR or ISSUES RESOLVED
- [ ] Numeric Quarantine complete — no `[NUMERIC GAP — not sourced]` flags remain
- [ ] All `[QA FLAG]` annotations resolved
- [ ] Triangulation Matrix `Numeric verified?` column complete with no `⚠`

If any item is unchecked, resolve it before generating the PDF.

### Step 8: PDF Generation
Compile into a professional PDF. Structure: RAG Dashboard → Critical Findings → Executive Summary → Purpose-Specific Brief → Full Analysis by section → Frameworks → Appendices (triangulation matrix, risk register, information gaps, monitoring plan, assumptions).

**Save the final PDF to the root of the company folder** (not inside `00-summary/`), named:
```
full-synthesis-report-YYYY-MM-DD-HH:MM.pdf
```
Where the timestamp is the investigation completion date and time in 24-hour format. Example: `full-synthesis-report-2026-03-03-14:35.pdf`. The timestamp allows multiple runs on the same day to coexist and makes it immediately clear when the intelligence was compiled. The working `synthesis.md` document stays in `00-summary/` as the source of truth; the PDF at root is the final polished deliverable.

---

## Folder Structure

**Folder naming:** Always use `_company-{slug}` format, where `{slug}` is the company name lowercased with spaces replaced by hyphens (e.g. `_company-greencollect`, `_company-westpac`, `_company-charter-hall`). The leading underscore keeps company folders sorted together and visually distinct from other project folders.

**Final synthesis report:** The completed PDF sits at the **root** of the company folder (not inside `00-summary/`), named `full-synthesis-report-YYYY-MM-DD-HH:MM.pdf` where the timestamp is the investigation completion date and time in 24-hour format. This makes it immediately findable and distinguishes multiple runs over time (e.g. `full-synthesis-report-2026-03-03-14:35.pdf`).

```
_company-{slug}/
├── full-synthesis-report-YYYY-MM-DD-HH:MM.pdf   ← FINAL DELIVERABLE — root level, timestamped with investigation completion time
├── 00-summary/
│   ├── intelligence-requirements.md
│   ├── company-scoping.md
│   ├── kit-answers.md
│   ├── synthesis.md                        (working document — source for PDF)
│   ├── rag-dashboard.md
│   ├── executive-summary.md
│   ├── critical-findings.md
│   ├── engagement-playbook.md              (if sales/BD)
│   ├── battle-cards/                       (if competitors identified)
│   ├── monitoring-plan.md
│   ├── adversarial-findings.md      ← output of adversarial search step
│   ├── assumptions-limitations.md
│   └── synthesis-source-register.md      ← claim-to-source linkage (Step 0, required before prose)
├── 01-identification/
├── 02-website/
├── 03-news-media/
│   ├── articles/
│   ├── videos/
│   ├── podcasts/
│   └── outstanding-media.md
├── 04-social-media/
├── 05-financial-legal/
│   ├── corporate-registration.md
│   ├── corporate-constellation.md
│   ├── financial-reports/
│   └── financial-analysis.md
├── 06-people/
│   └── [person-name]-profile.md
├── 07-reputation/
├── 08-digital-footprint/
│   ├── dns-infrastructure.md
│   ├── metadata-findings.md
│   └── website-archaeology.md
├── 09-customers-stakeholders/
│   ├── beneficiary-analysis.md             (if SE/NFP)
│   └── value-flow-map.md                   (if SE/NFP)
├── 10-industry-market/
├── 11-revenue-opportunities/               (if revenue discovery mode)
├── inaccessible-sources.md          ← sources that failed all four layers
├── research-log.md
└── INDEX.md
```

Every subfolder gets an INDEX.md cataloguing its contents with source, date, confidence rating, and summary.

---

## Parallel Execution Strategy

Read `company-agent-dispatch.md` for full wave parallelisation guidance: agent briefing templates, handoff format, tier effort caps, and timeout fallback.

**Wave structure summary:**
- **Wave 1:** Phase 1 (Identification + entity type classification) — must complete first
- **Wave 2 (parallel):** Phase 2 (Website) + Phase 3 (News) + Phase 4 (LinkedIn) + Phase 5 (Registry core)
- **Wave 2 threshold:** If entity verification returns fewer than 2 independent sources confirming the entity, or any KIT has zero substantive findings, pause and report before Wave 3
- **Wave 3 (parallel):** Phase 4b (Other social) + Phase 6 (People) + Phase 7 (Reputation) + Phase 8 (Digital footprint) + Phase 5 (Financial/legal deep)
- **Wave 4 (parallel):** Phase 9 (Customers) + Phase 10 (Industry)
- **Wave 5:** Phase 11 (Synthesis + Expert QA)

---

## Progress Reporting

See `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` Section 6 for the mandatory wave summary format. Post after every wave before proceeding to the next. Not optional.

---

## Research Log Format

See `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` Section 13 for the standard research log format. Append to `research-log.md` throughout the investigation.

**company-intel addition:** Each entry that records ASIC, ACNC, or other registry data must include: `Last-lodged date: [date]` and `Data-currency risk: [high / medium / low]`.

---

## Confidence Rating System

See `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` Section 4 for the full confidence rating system and source independence rule. Apply ★★★/★★/★/⚠ ratings to every piece of information recorded.

**Source independence matters.** Two sources citing the same original report = one source.

---

## Source Saturation Rule

See `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` Section 5 for the source saturation rule. When two consecutive search queries on the same subject area return no new sources, declare saturation for that area and move on.

Saturation is a valid finding — note it explicitly in the relevant phase file and in the Information Gaps output.

---

## Refresh Investigation Protocol

When updating an existing dossier (Menu option 3):

1. Load `00-summary/company-scoping.md` — reload original KITs and entity type module
2. Load `research-log.md` and `00-summary/kit-answers.md` — identify what was answered and what was partial
3. Load `00-summary/monitoring-plan.md` — check if any trigger events have fired since last run
4. Determine refresh scope:
   - Which KITs were `partial` or `unanswered` -> re-run those phases fully
   - Which phases are time-sensitive (news, LinkedIn, ASIC filings) -> run regardless of prior status
   - Which phases are stable (website architecture, digital footprint) -> carry forward unless a trigger event fired
5. Run only the scoped phases — do not re-run the full investigation
6. Apply the data-currency warning: for any ASIC or ACNC data carried forward, flag the last-lodged date and assess whether it may have changed
7. If a refresh finding materially contradicts a prior KIT answer, do not silently update — flag the contradiction explicitly in `kit-answers.md` with: `[CHANGED — prior: X, now: Y, date of change: YYYY-MM-DD]`
8. Update: `kit-answers.md`, `critical-findings.md`, `rag-dashboard.md`, `monitoring-plan.md`
9. Append a refresh block to `research-log.md`:

```markdown
## Refresh — [YYYY-MM-DD]
What was refreshed: [phases re-run]
What was carried forward: [phases not re-run and why]
Material changes: [what changed vs. prior run — especially any KIT status changes]
Contradictions found: [if any refresh finding contradicts a prior KIT answer, list them here]
Next refresh: [date or trigger event]
```

10. Regenerate the PDF only if findings have materially changed.

---

## Key Principles

1. **Decision-relevance over comprehensiveness.** Orient everything toward the user's stated purpose.
2. **Provenance on everything.** Every fact cites its source with a confidence rating.
3. **Independent sources matter.** Two company press releases ≠ two sources.
4. **Gaps are intelligence.** What's missing is as important as what's found. Interpret every gap.
5. **The "Inversion Question."** For key claims, ask: "What would the evidence look like if the opposite were true?"
6. **Forward-looking, not just backward-looking.** Include scenario analysis, early warning indicators, and "So What?" implications.
7. **Actionable outputs.** The person reading this should know what to DO, not just what to THINK.
8. **Expert QA.** Route synthesis through relevant expert panels before finalising.
9. **Be transparent about limitations.** State assumptions, note stale data, flag access limitations.
10. **Ethical boundaries.** All intelligence from publicly accessible sources only. No misrepresentation of identity. No access to authenticated systems. Compliance with Privacy Act and applicable legislation.
- **Universal Layer 4 fallback.** If Layers 1–3 fail, always try Playwright before declaring a source inaccessible. This applies to ACNC, Glassdoor, Facebook, ASIC Connect, gov.au pages, and any other source that fails direct WebFetch.
