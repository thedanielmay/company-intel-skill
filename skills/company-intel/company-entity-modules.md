# Company Entity Modules

## Purpose

Entity-type routing for company-intel investigations. When Phase 0 classifies the target entity, load the matching module. The module defines KIT defaults, source priorities, phase emphasis, and output format.

Read this file at Phase 0 Step 2 (after entity is confirmed, before KIT elicitation).

---

## Entity Classification

Classify the entity on intake. If ambiguous between two types, present both options and ask the user to confirm.

| Code | Entity type | Identifiers |
|---|---|---|
| STA | Startup / early-stage | Founded <5 years, private, no public financials, VC or angel-backed |
| SME | Private SME | Founded 5+ years, private, owner-operated or PE-light, <200 staff |
| ASX | ASX-listed company | Listed on ASX — public financials, disclosure requirements apply |
| PEQ | PE-backed or VC-backed (mature) | Private, institutional ownership, likely preparing for exit or IPO |
| NFP | NFP, charity, or social enterprise | ACNC-registered, ABN entity type = charity/association |
| GOV | Government agency or statutory body | Commonwealth, state, or local government entity |
| FOR | Foreign subsidiary or branch | Parent entity is overseas, Australian registered subsidiary |

---

## Module STA — Startup / Early-Stage

**Default KITs:**
1. Who founded this company and what is their track record?
2. What problem are they solving, for whom, and what is the evidence it works?
3. How are they funded — who has invested, at what valuation, and how much runway do they likely have?
4. Who are their early customers and what do early users say?
5. What is the competitive landscape and where does this startup sit in it?

**Source priorities (in order):**
- Crunchbase / PitchBook (funding history, investors, valuation rounds)
- LinkedIn (founder profiles, team composition, growth trajectory)
- Product Hunt, AppSumo, Hacker News (launch reception, early user feedback)
- AngelList, startup directories
- ASIC (basic registration) — note: financial data will be sparse or nil
- VC firm portfolio pages (confirm investment, sometimes include commentary)
- Media (TechCrunch AU, StartupDaily, SmartCompany)
- ProductReview, G2, Capterra, App Store (user feedback)

**Phase emphasis:**
- Phase 6 (People) — highest priority: founders are the company at this stage
- Phase 3 (News/Media) — moderate: coverage is often sparse but launch press matters
- Phase 5 (Financial/Legal) — minimal: expect nil financials; focus on registration only
- Phase 4 (LinkedIn) — high priority: team composition is a key signal

**Phase 5 note (data-currency warning):** ASIC registration data for startups is current as of registration date and any lodged documents. No financial disclosures are required for proprietary limited companies — absence of financials is expected, not a gap.

**Output variant:** Startup Intelligence Brief — team, funding, product-market fit signals, competitive positioning, early user sentiment, investment readiness signals.

---

## Module SME — Private SME

**Default KITs:**
1. Who owns and runs this business, and what is their background?
2. What is the business's financial health — revenue trajectory, profitability signals, and debt position?
3. Who are their customers and how do they acquire them?
4. What is their reputation in the market — clients, employees, and community?
5. What are the key risks — financial, operational, legal, or reputational?

**Source priorities:**
- ASIC company extract (directors, registered office, share structure, document history)
- ABR (entity type, GST registration, Historical Details tab)
- PPSR (Personal Property Securities Register — charges against assets, insolvency signal)
- AusTender + state procurement portals (government contract history)
- LinkedIn (team, growth, employee reviews)
- Glassdoor (employee sentiment)
- ACCC enforcement register (if relevant sector)
- AustLII (court records, Fair Work decisions)
- Local media, industry press

**Phase emphasis:**
- Phase 5 (Financial/Legal) — highest priority: ASIC extract, PPSR, procurement history
- Phase 6 (People) — high: owner-operated = people ARE the business
- Phase 7 (Reputation) — high: Glassdoor and reviews matter more here than for larger entities

**Phase 5 note (data-currency warning):** ASIC data reflects filings as of lodgement date. Director changes, share transfers, and address updates may lag by weeks to months. Always check the "Document History" tab for recent filings and note the last-lodged date. Rate ASIC-derived structural information as ★★★ for official status but flag the potential recency lag.

**Output variant:** SME Intelligence Brief — ownership and control, financial health signals, customer and procurement profile, reputational picture, key risks.

---

## Module ASX — ASX-Listed Company

**Default KITs:**
1. What is the company's financial performance and trajectory — revenue, margins, cash position?
2. What is the market's view — how does the share price and analyst consensus compare to fundamentals?
3. Who are the significant shareholders and what are their interests?
4. What are the material risks disclosed — and what is not being disclosed that competitors are?
5. What is the board and management quality — track record, independence, remuneration alignment?

**Source priorities:**
- ASX announcements (market sensitive disclosures, annual reports, investor presentations) — Layer 1 API
- ASIC Connect (company extract, director history)
- Annual Report and Half-Year Report (full financial statements)
- Concise Annual Report (management narrative)
- Investor relations website (presentations, transcripts)
- Analyst reports (broker notes — check for free summaries)
- Morningstar, Simply Wall St (financial data aggregators)
- AFR, The Australian (business media coverage)
- ACCC, ASIC enforcement register

**Phase emphasis:**
- Phase 5 (Financial/Legal) — highest priority: full ASX filings regime makes this the richest data phase
- Phase 10 (Industry/Market) — high: listed companies compete in well-defined markets with public benchmarks
- Phase 9 (Customers/Stakeholders) — high: institutional shareholders are a critical stakeholder group

**Phase 5 note (data-currency warning):** ASX continuous disclosure obligations mean material information must be lodged within 24 hours. However, operational details between announcements may be months stale. Flag the date of each ASX filing used. For financial data, note that half-year results lag 6 months and annual results lag 12 months from the relevant period.

**Output variant:** Listed Company Intelligence Brief — financial performance analysis, shareholder register analysis, board quality assessment, market positioning, disclosure gaps, analyst consensus vs. evidence.

---

## Module PEQ — PE-Backed / VC-Backed (Mature)

**Default KITs:**
1. Who owns this business — who are the PE/VC investors, what is their fund strategy, and when do they need an exit?
2. What is the fund's investment thesis for this company — what transformation are they driving?
3. What is the financial profile — EBITDA signals, debt load, add-on acquisition history?
4. Who has been brought in to lead — are these exit-oriented executives or operators?
5. What is the exit pathway and timeline — IPO, trade sale, secondary PE?

**Source priorities:**
- ASIC company extract (complex share structure is often a PE signal)
- PitchBook / Crunchbase (ownership chain, fund vintage, portfolio context)
- PE firm website (portfolio page, investment thesis, sector focus)
- LinkedIn (management changes — PE often installs new C-suite)
- AusTender (government contract history — common PE growth lever)
- AFR Deal Book, Australian PE/VC sector media
- Glassdoor (culture change signals post-acquisition)
- AustLII (any M&A-related litigation)

**Phase emphasis:**
- Phase 6 (People) — high: tracking management changes reveals investment thesis in action
- Phase 5 (Financial/Legal) — high: PPSR charges are particularly important (PE debt structures)
- Phase 8 (Digital Footprint) — moderate: website changes post-acquisition signal repositioning

**Phase 5 note (data-currency warning):** PE-backed companies have minimal public financial disclosure. ASIC extract will show structure but not financials. PPSR is the most reliable financial signal — security interests registered there reflect actual debt load as of registration date. Flag all financial estimates as ★ (inferred) unless from a disclosed source.

**Output variant:** PE Intelligence Brief — ownership map, fund strategy and timeline, management profile, financial signals, exit pathway assessment, engagement implications.

---

## Module NFP — NFP, Charity, or Social Enterprise

**Default KITs:**
1. What is the mission and how effectively is it being delivered against stated outcomes?
2. What is the financial health — revenue diversification, reserves, grant cliff risk?
3. Who governs and manages the organisation — board composition, independence, executive quality?
4. What is the organisation's reputation with beneficiaries, funders, and community?
5. What are the compliance and regulatory obligations — ACNC requirements, sector-specific regulation?

**Source priorities:**
- ACNC charity register (full extract, financial reports, governance, beneficiaries, compliance history)
- ABN Lookup (entity type, DGR status, tax concessions)
- GrantConnect + state grant portals (funding history, grants received)
- AusTender (government contract history)
- Social Traders certification register (for certified social enterprises)
- NDIS Commission register (if applicable)
- Aged Care Quality register (if applicable)
- ACNC Annual Information Statements (AIS) — governance declarations
- Pro Bono Australia, The Mandarin (sector media)
- Glassdoor (staff sentiment — particularly relevant in NFP for mission/management alignment)

**Phase emphasis:**
- Phase 5 (Financial/Legal) — highest priority: ACNC financials are the richest source
- Phase 9 (Customers/Stakeholders) — high: beneficiary community and funder ecosystem
- Phase 7 (Reputation) — high: community standing matters more here than commercial reputation

**Phase 5 note (data-currency warning):** ACNC financial reports have a 12-18 month publication lag (must be lodged 6 months after financial year end). Rate ACNC financial data as ★★★ for accuracy but flag the lag explicitly. A 2024 ACNC report reflects financial position as of June 2023 — material change in the intervening period is possible and should be flagged.

**Output variant:** NFP Intelligence Brief — mission delivery assessment, financial health scorecard (reserves ratio, revenue concentration, grant cliff risk), governance quality, community standing, compliance profile.

---

## Module GOV — Government Agency or Statutory Body

**Default KITs:**
1. What is this agency's mandate, scope of powers, and legislative basis?
2. Who leads the agency — secretary/CEO, board, key executives?
3. What is the agency's budget and funding history — is it growing or declining?
4. What decisions, enforcement actions, or policy outputs has this agency produced recently?
5. What stakeholder relationships shape this agency's behaviour — peak bodies, ministers, regulated entities?

**Source priorities:**
- Enabling legislation (legislation.gov.au or state equivalent) — primary instrument
- Portfolio Budget Statements (federal agency funding — budget.gov.au)
- Annual Reports (ANAO-audited, most recent 3 years)
- ANAO performance audits of this agency
- Hansard (Senate Estimates transcripts are gold — public questioning of agency heads)
- Ministers' media releases (political direction signals)
- Senate Standing Committee reports (committee scrutiny)
- AusTender (procurement patterns reveal operational priorities)
- Agency website (current structure, publications, consultation register)

**Phase emphasis:**
- Phase 5 (Financial/Legal) — high: budget data, audit findings, enabling legislation
- Phase 3 (News/Media) — high: media coverage of enforcement actions, budget decisions
- Phase 9 (Customers/Stakeholders) — high: regulated industry as primary stakeholder

**Phase 5 note (data-currency warning):** Annual Reports are published 3-4 months after financial year end. Portfolio Budget Statements reflect budget-year decisions. Senate Estimates occur twice yearly — check the most recent session for up-to-date agency positioning.

**Output variant:** Government Agency Intelligence Brief — mandate and powers, leadership, budget trajectory, recent decisions and enforcement actions, political context, stakeholder landscape.

---

## Module FOR — Foreign Subsidiary or Branch

**Default KITs:**
1. Who is the ultimate parent entity and what is their global business?
2. What is the Australian subsidiary's role — sales office, full operations, manufacturing, R&D?
3. How financially material is the Australian operation to the parent?
4. Who runs the Australian operation and what authority do they have?
5. What regulatory obligations apply to the Australian entity specifically?

**Source priorities:**
- ASIC company extract (foreign company registration, local directors, annual return)
- ABR (Australian entity type, ABN, GST registration)
- Parent company annual report (look for Australia references, segment data)
- Parent's investor relations filings (if listed — 10-K/20-F for US-listed parents)
- LinkedIn (Australian team size, local leadership)
- AusTender (local procurement history)
- ACCC (merger decisions, enforcement — relevant for market entry)
- FIRB decisions (if relevant — foreign investment approval history)

**Phase emphasis:**
- Phase 5 (Financial/Legal) — high: parent company filings are the primary financial source
- Phase 6 (People) — high: local leadership authority is often opaque without this
- Phase 1 (Identification) — critical: must confirm Australian entity and map to parent

**Phase 5 note (data-currency warning):** Australian subsidiary financial disclosures are minimal for foreign-owned entities. Parent company filings are authoritative but may not break out Australian operations. Rate Australian-specific financial estimates as ★ (inferred from parent disclosures) unless a subsidiary annual return has been filed.

**Output variant:** Foreign Subsidiary Intelligence Brief — parent entity profile, subsidiary role and authority, local financial signals, Australian leadership, regulatory position, engagement implications (local vs. headquarters decision-making).
