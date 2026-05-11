# Company Expert Panels

## Purpose

Provides embedded QA expert personas for Phase 11 synthesis review. Distinct from the interactive `expert-panel` skill — these are structured reviewers applied during synthesis, not a full adversarial panel session.

Read this file at the start of Phase 11 (Synthesis) for every Full Investigation (Tier 3). Select the expert set matching the entity type classified in Phase 0.

---

## Integration Modes

### Mode 1 — Synthesis Reviewer (default, always invoke for Full Investigations)

During Phase 11, before generating any deliverable, route the draft synthesis through the 2-3 most relevant experts for the entity type. Each expert reviews their domain and flags gaps, weak analysis, or missing intelligence.

**When:** Always, during Phase 11 synthesis. Select experts matching the entity module.

### Mode 2 — On-Demand Consultant

Available during any research phase when unexpected findings, thin results, or contradictory information appear in a specific expert's domain. Invoke by asking: "What would [Expert Name] look for here?"

**When:** When a phase produces unexpected, thin, or contradictory results in a specific domain.

### Mode 3 — Pre-Output QA (Full Investigation only)

Before generating the final PDF synthesis, route the complete dossier through ALL three experts for the entity type. Each reviews the full output from their perspective and flags critical omissions as `[QA FLAG]` annotations.

**When:** Always, as the final step before invoking `document-skills:pdf`. Reviews outputs only — does not re-run research phases.

---

## Expert Sets by Entity Module

### STA — Startup / Early-Stage

**Expert 1: Startup Investor**
- Persona: Partner at an Australian VC or early-stage fund, 12+ years evaluating and backing startups across tech, climate, and enterprise software sectors
- Domain: Funding history accuracy, team quality signals, product-market fit evidence, runway and burn assessment
- Key questions:
  - "Is the funding history consistent across Crunchbase, LinkedIn, and media — or are there discrepancies?"
  - "Has the founding team's prior track record been verified, not just described?"
  - "Is product-market fit assessed from user evidence or from the company's own claims?"
  - "Has burn rate been estimated — does the funding runway match the team size and spend signals?"
  - "Have the co-investors been profiled — do they signal smart money or warm money?"
- Will challenge: PMF claims without user evidence, funding history from company self-report only, missing competitor context
- Invoke in Mode 2 when: Phase 6 (People) returns thin founder track record, or funding history cannot be verified across two independent sources

**Expert 2: Early-Stage Customer**
- Persona: Head of Innovation or technology buyer at an ASX200 enterprise, 10+ years evaluating and piloting emerging technology vendors
- Domain: Enterprise readiness signals, user evidence quality, reference customer credibility, procurement risk
- Key questions:
  - "Are the reference customers named — and are they credible validators for this company's claims?"
  - "Has the product been independently reviewed — G2, Capterra, App Store reviews?"
  - "Is there evidence of renewal — or only evidence of first sales?"
  - "Have the integration and security requirements been assessed from a buyer's perspective?"
  - "What is the exit risk — what happens to the customer if this startup fails?"
- Will challenge: Customer proof from company case studies only, missing independent user reviews, enterprise readiness not assessed
- Invoke in Mode 2 when: Phase 9 (Customers) returns only company-provided testimonials

**Expert 3: Technical Due Diligence Analyst**
- Persona: CTO or principal engineer with 15+ years, 5+ years conducting technical due diligence for PE/VC
- Domain: Technology stack quality, IP ownership, technical team depth, code quality signals
- Key questions:
  - "Has the GitHub or public code repository been reviewed for team size, commit activity, and code quality signals?"
  - "Is the technology proprietary or commodity — is there a defensible IP moat?"
  - "Has the technical team been assessed separately from the founding team?"
  - "Are there any patents filed — and are they granted or only applied for?"
  - "Has the infrastructure dependency map been assessed — is this AWS-native with standard tooling, or is there custom infrastructure risk?"
- Will challenge: Technology claims without technical evidence, IP described without checking patent register, team depth not assessed beyond founders
- Invoke in Mode 2 when: Phase 8 (Digital Footprint) does not include code repository analysis

---

### SME — Private SME

**Expert 1: SME Credit Analyst**
- Persona: Senior credit analyst at a major Australian bank, 12+ years assessing SME lending risk
- Domain: Financial health signals, debt position, PPSR charges, cash flow proxies, insolvency risk
- Key questions:
  - "Has PPSR been checked for registered charges — security interests reveal the debt load?"
  - "Have the ASIC document filings been checked for late lodgements — a pattern of late lodgement signals financial stress?"
  - "Has the government contract history (AusTender) been used to proxy revenue — and has it trended up or down?"
  - "Are there any director disqualifications or related-entity insolvencies in the ownership network?"
  - "Has the industry-specific credit risk been assessed — some sectors have structural default rates?"
- Will challenge: Financial assessment without PPSR, missing director disqualification check, no proxy revenue estimate
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) is thin on financial signals or PPSR was not accessed

**Expert 2: Fair Work and Employment Lawyer**
- Persona: Senior employment lawyer, 12+ years advising SMEs and employees on Fair Work matters
- Domain: Employment compliance, Fair Work Commission decisions, contractor classification, underpayment risk
- Key questions:
  - "Has the Fair Work Commission decision register been searched for decisions involving this employer?"
  - "Has the ASIC banned and disqualified register been checked for all current and historical directors?"
  - "Has Modern Slavery Act reporting been checked — applies to entities with >$100m revenue?"
  - "Are there known underpayment investigations — ASIC or media reports?"
  - "Has the employment model been assessed — high contractor use may signal classification risk?"
- Will challenge: Legal section that only covers litigation, missing Fair Work and employment compliance angle
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not include Fair Work Commission search

**Expert 3: B2B Sales Director**
- Persona: State sales director at a professional services firm, 15+ years selling to SMEs and mid-market
- Domain: Customer acquisition and retention signals, procurement patterns, buying centre mapping
- Key questions:
  - "Has the customer profile been built from evidence — procurement records, case studies, directory listings — or inferred?"
  - "Is there a government procurement component — AusTender and state portal history?"
  - "Have the sales channels been identified — direct, channel partner, platform?"
  - "Is there evidence of customer concentration risk — do 1-3 customers make up most revenue?"
  - "Has the sales leadership been assessed — is there a CRO or VP Sales, or is the founder still selling?"
- Will challenge: Customer section built from website testimonials only, missing procurement history analysis
- Invoke in Mode 2 when: Phase 9 (Customers) does not include AusTender search

---

### ASX — ASX-Listed Company

**Expert 1: Equity Research Analyst**
- Persona: Senior equity analyst covering ASX-listed companies, 12+ years at a major investment bank or research house
- Domain: Financial performance analysis, analyst consensus, valuation, capital allocation, earnings quality
- Key questions:
  - "Has the financial analysis used the full financial statements — P&L, balance sheet, and cash flow — or only headline figures?"
  - "Has the earnings quality been assessed — are reported earnings inflated by non-cash items or one-off gains?"
  - "Has revenue by segment been analysed where disclosed?"
  - "Has the capital allocation track record been assessed — acquisitions, buybacks, dividend policy?"
  - "Is the analyst consensus captured — and has it been compared to the company's own guidance?"
- Will challenge: Financial summary without cash flow analysis, no earnings quality assessment, missing analyst consensus context
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not include cash flow analysis

**Expert 2: Corporate Governance Specialist**
- Persona: Senior governance advisor at a proxy advisory firm (ISS, CGI Glass Lewis), 10+ years advising institutional shareholders
- Domain: Board composition, independence, remuneration alignment, related party transactions, disclosure quality
- Key questions:
  - "Has the board composition been assessed for independence — are the independent directors genuinely independent?"
  - "Has the executive remuneration structure been assessed for alignment with long-term shareholder value?"
  - "Are there related party transactions disclosed — and are they on arm's length terms?"
  - "Has the company's disclosure quality been assessed — do they disclose more or less than required?"
  - "Have any significant votes against management resolutions at the AGM been noted?"
- Will challenge: Board section that only describes rather than assesses, no remuneration structure analysis, missing related party transaction check
- Invoke in Mode 2 when: Phase 6 (People) does not assess board independence

**Expert 3: Institutional Investor Relations Advisor**
- Persona: Senior IR advisor with 12+ years working with ASX-listed companies and institutional investors
- Domain: Shareholder register, institutional sentiment, retail vs. institutional composition, activist risk
- Key questions:
  - "Has the shareholder register been mapped — who are the substantial holders and what are their interests?"
  - "Have any activist or activist-adjacent shareholders been identified?"
  - "Has the trading pattern been assessed — is there unusual volume or short interest?"
  - "Have the institutional holders been compared to sector peers — are the right funds holding this stock?"
  - "Has any recent change in register been identified — are long-term holders selling?"
- Will challenge: People section that misses major shareholders as key stakeholders, no register analysis
- Invoke in Mode 2 when: Phase 9 (Customers/Stakeholders) does not map the shareholder register

---

### PEQ — PE-Backed / VC-Backed (Mature)

**Expert 1: PE Investment Professional**
- Persona: Principal or Director at an Australian PE fund, 10+ years executing buyouts and portfolio company transformations
- Domain: Ownership structure, fund strategy and vintage, exit timeline, value creation thesis
- Key questions:
  - "Has the fund vintage been identified — a 2019 fund is under exit pressure; a 2023 fund is still building?"
  - "Has the ownership chain been traced to the ultimate fund entity?"
  - "Have other portfolio companies in the same fund been identified — do they signal a pattern?"
  - "Has the management team composition been compared to pre-acquisition — how many were replaced?"
  - "Have add-on acquisitions been identified via ASIC and media — they are a primary PE value creation lever?"
- Will challenge: PE ownership described without fund vintage, missing portfolio pattern analysis, no management change tracking
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not trace ownership to ultimate fund entity

**Expert 2: Portfolio Company CFO**
- Persona: CFO with experience at 3+ PE-backed portfolio companies, 15+ years in private company finance
- Domain: PE financial structures, debt covenants, EBITDA management, management incentive plans
- Key questions:
  - "Has PPSR been checked for the debt security structure — PE deals involve significant leverage?"
  - "Has the EBITDA proxy been estimated — multiple of revenue and cost signals?"
  - "Are there management incentive plan signals — LinkedIn titles like 'Principal' or 'Partner' on the leadership team?"
  - "Has the acquisition price been estimated from available signals (multiples, sector comparables)?"
  - "Are there cost-out signals — Glassdoor reviews mentioning restructuring, job postings showing role rationalisation?"
- Will challenge: PE financial analysis without PPSR or debt structure assessment, no EBITDA estimation
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not include PPSR or proxy financial analysis

**Expert 3: M&A Lawyer**
- Persona: Partner at a top-tier M&A practice, 15+ years advising on PE transactions and portfolio company exits
- Domain: Corporate structure, ASIC compliance, pre-exit preparation signals, legal risk in portfolio companies
- Key questions:
  - "Has the ASIC document history been checked for recent restructuring activity — amalgamations, share transfers?"
  - "Has the registered charge history been checked — PPS Register reveals lender security interests?"
  - "Have any litigation signals been identified — a company preparing for exit cleans up legal issues?"
  - "Have any ASIC compliance issues been flagged — late lodgements in a PE company are unusual and signal problems?"
  - "Has the company structure complexity been assessed — multiple layers of SPVs and holding companies are a red flag?"
- Will challenge: Legal section without ASIC document history review, no charge registration analysis
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not review ASIC document history for recent activity

---

### NFP — NFP, Charity, or Social Enterprise

**Expert 1: NFP Financial Analyst**
- Persona: Senior auditor or financial advisor, 12+ years working exclusively with charities and NFPs in Australia
- Domain: ACNC financials, revenue diversification, reserves adequacy, grant cliff risk, financial sustainability
- Key questions:
  - "Has the revenue concentration been analysed — what share comes from the top 1, 3, and 5 funding sources?"
  - "Has the reserves ratio been calculated — how many months of operating expenditure are held in unrestricted reserves?"
  - "Has the grant cliff risk been assessed — are major grants ending in the next 12-24 months?"
  - "Has the workforce cost ratio been checked — for most social services NFPs, it should be 55-75%?"
  - "Has the ACNC Annual Information Statement been reviewed for governance declarations?"
- Will challenge: Financial section without reserves ratio, no grant cliff analysis, workforce cost ratio not calculated
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not calculate reserves ratio or revenue concentration

**Expert 2: Social Impact Evaluator**
- Persona: Senior evaluator or impact measurement specialist, 10+ years designing and assessing social impact programs
- Domain: Mission delivery evidence, outcome measurement, program logic, beneficiary voice
- Key questions:
  - "Is the mission delivery assessed from independent evidence — evaluation reports, ACNC AIS outcomes — or from the organisation's own claims?"
  - "Has the beneficiary voice been represented in the intelligence — what do beneficiaries say, not just funders and management?"
  - "Has the theory of change been articulated — is there a logical pathway from activities to outcomes?"
  - "Have the counterfactual claims been assessed — would beneficiaries achieve similar outcomes without this organisation?"
  - "Have the organisation's self-reported impact metrics been triangulated against any independent evidence?"
- Will challenge: Mission delivery section built entirely from the organisation's own materials, no independent evaluation evidence
- Invoke in Mode 2 when: Phase 9 (Customers/Stakeholders) Beneficiary Analysis section is thin or sourced only from organisation materials

**Expert 3: Community Sector Regulator**
- Persona: Former ACNC investigator or state peak body compliance officer, 10+ years in NFP governance and compliance
- Domain: ACNC compliance, governance obligations, sector-specific regulation, related entity complexity
- Key questions:
  - "Has the ACNC compliance history been checked — any formal warnings, compliance agreements, or revocations?"
  - "Has the related entity structure been mapped — NFPs often have complex structures with trading arms, subsidiaries, and associated entities?"
  - "Have the sector-specific regulatory obligations been identified — NDIS, Aged Care, Housing, Mental Health?"
  - "Has the board composition been assessed for governance obligations — skills, independence, declared conflicts?"
  - "Have the annual reporting obligations been met — is the most recent AIS lodged and publicly available?"
- Will challenge: Compliance section without ACNC compliance history, complex group structure not mapped, no sector-specific regulatory check
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not check ACNC compliance history or group structure

---

### GOV — Government Agency or Statutory Body

**Expert 1: Public Sector Auditor**
- Persona: Senior performance auditor at ANAO or a state audit office (VAGO, NSWAO), 12+ years conducting performance and financial audits
- Domain: Budget accuracy, audit findings, program effectiveness, financial management quality
- Key questions:
  - "Have ANAO or state audit body performance audits of this agency been located and reviewed?"
  - "Has the budget trend been checked against Portfolio Budget Statements for 3+ years?"
  - "Have any qualified audit opinions been identified in the agency's financial statements?"
  - "Has the proportion of discretionary vs. statutory spending been assessed — this shapes the agency's flexibility?"
  - "Has the Senate Estimates transcript history been checked — agencies reveal operational details under questioning?"
- Will challenge: Budget analysis without multi-year trend, no audit history review, Senate Estimates not searched
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not reference Portfolio Budget Statements or ANAO

**Expert 2: Regulatory Policy Advisor**
- Persona: Former senior policy officer or regulatory advisor, 15+ years at federal or state government agencies
- Domain: Legislative mandate, ministerial relationship, policy direction, regulatory culture
- Key questions:
  - "Has the enabling legislation been directly accessed — not described from secondary commentary?"
  - "Has the current Minister's stated policy direction for this agency been captured — ministerial speeches and media releases?"
  - "Has the agency's enforcement culture been assessed — proactive vs. reactive, principle-based vs. rules-based?"
  - "Have the agency's formal consultation documents been reviewed — these reveal its working priorities?"
  - "Is there evidence of any tension between the agency's mandate and its current political direction?"
- Will challenge: Policy section built from agency website rather than primary legislation and ministerial direction
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not reference enabling legislation directly

**Expert 3: Senate Estimates Specialist**
- Persona: Senior parliamentary adviser or journalist who covers Senate Estimates, 10+ years tracking agency accountability
- Domain: Agency accountability, political pressure, leadership under scrutiny, disclosed vs. undisclosed problems
- Key questions:
  - "Have the most recent 2-3 Senate Estimates transcripts been reviewed for this agency?"
  - "Have any Senate committee recommendations directed at this agency been found — and has the agency responded?"
  - "Have any FOI disclosures involving this agency been located via Right to Know (righttoknow.org.au)?"
  - "Has media coverage of the agency's Senate appearances been reviewed?"
  - "Have whistleblower or protected disclosure signals been checked — public interest disclosures sometimes surface in media?"
- Will challenge: Government agency brief without Senate Estimates analysis, no FOI disclosure check
- Invoke in Mode 2 when: Phase 3 (News/Media) does not include Senate Estimates coverage

---

### FOR — Foreign Subsidiary or Branch

**Expert 1: International M&A and FDI Advisor**
- Persona: Senior cross-border M&A advisor or foreign investment specialist, 12+ years advising on inbound investment to Australia
- Domain: Parent entity profile, subsidiary role, FIRB implications, capital repatriation structures
- Key questions:
  - "Has the parent entity's annual report been reviewed for Australia-specific references?"
  - "Has FIRB clearance been confirmed — foreign acquisitions above threshold require FIRB approval?"
  - "Has the repatriation structure been considered — intercompany loans and management fees affect Australian entity economics?"
  - "Is the subsidiary financially material to the parent — or is Australia a small market for them?"
  - "Has the parent's strategic intent for Australia been assessed — growth, maintenance, or exit?"
- Will challenge: Foreign subsidiary analysis that doesn't reference parent entity filings, no FIRB check
- Invoke in Mode 2 when: Phase 5 (Financial/Legal) does not review parent entity filings

**Expert 2: Australian Corporate Lawyer**
- Persona: Partner at an Australian law firm, 12+ years advising foreign entities operating in Australia
- Domain: Australian regulatory obligations for foreign companies, ASIC foreign company registration, local director requirements
- Key questions:
  - "Has the ASIC foreign company extract been reviewed — local directors and registered office are required?"
  - "Have the Australian regulatory obligations been assessed — does this entity need an AFS licence, ACL, or other Australian authorisation?"
  - "Has the transfer pricing risk been considered — ATO scrutiny of related-party transactions between parent and subsidiary?"
  - "Has the employment structure been reviewed — is the Australian entity employing local staff directly?"
  - "Have the local director obligations been confirmed — at least one Australian resident director is required?"
- Will challenge: Foreign subsidiary profile without ASIC foreign company registration review, no Australian regulatory obligation assessment
- Invoke in Mode 2 when: Phase 1 (Identification) does not confirm Australian registered entity type

**Expert 3: Country Manager / Regional Director**
- Persona: Experienced country manager or regional director, 15+ years leading Australian operations of international companies
- Domain: Local authority and decision-making power, commercial autonomy, Australian team quality, HQ relationship
- Key questions:
  - "Has the local leadership's authority level been assessed — do they have P&L responsibility or are they a sales office?"
  - "Has the Australian team size and composition been estimated from LinkedIn?"
  - "Has the headquarters relationship been assessed — how much local autonomy does the Australian operation have?"
  - "Have the local commercial achievements been identified — growth, contracts won, market position?"
  - "Is there evidence of tension between local needs and HQ direction — Glassdoor often surfaces this?"
- Will challenge: Foreign subsidiary brief that describes the parent but not the local team authority and autonomy
- Invoke in Mode 2 when: Phase 6 (People) does not assess local leadership authority relative to parent entity
