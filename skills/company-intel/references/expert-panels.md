> **Superseded for Phase 11 QA:** The entity-type expert panels used for Phase 11 Synthesis QA are now in `~/.claude/skills/company-intel/company-expert-panels.md`. Use that file for Modes 1, 2, and 3 QA review.
>
> This file retains the purpose-based expert personas (due diligence, sales/BD, social enterprise) for use in the interactive `expert-panel` skill session, or when Phase 11 QA for a specific purpose orientation is needed beyond the entity-type panels.

---

# Expert Review Panels

Six expert personas embedded into the company-intel skill. These experts provide quality assurance, analytical depth, and decision-relevance across three integration modes.

## Integration Modes

### Mode 1: Synthesis Reviewers (Default)
During Phase 11 (Synthesis), before generating the final output, route the draft synthesis through relevant experts based on investigation purpose. Each expert reviews their domain and flags gaps, weak analysis, or missing intelligence.

**When to invoke:** Always, during synthesis. Select 2-3 most relevant experts based on the user's stated purpose (from Phase 0).

### Mode 2: On-Demand Consultants
Available during any phase when the investigator encounters domain-specific complexity. Invoke by asking: "What would [Expert] look for here?"

**When to invoke:** When a phase produces unexpected findings, thin results, or contradictory information in a specific expert's domain.

### Mode 3: Quality Assurance (Pre-Output)
Before generating the final PDF synthesis, run a QA pass through ALL experts. Each reviews the complete dossier from their perspective and flags critical omissions.

**When to invoke:** Always, as the final step before PDF generation. Flag any issues found as `[QA FLAG]` annotations in the synthesis.

**Mode 3 scope:** Mode 3 QA covers the full synthesis output — all deliverables listed in `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §9, plus all company-intel-specific outputs (RAG Dashboard, Engagement Playbook, Competitive Profile). It does NOT re-run research phases; it reviews the outputs of Phase 11 synthesis only.

---

## The Six Experts

### 1. Competitive Intelligence Analyst
**Persona:** Senior CI practitioner, 15 years at firms like Kroll, FTI Consulting, and McKinsey competitive strategy.

**Domain:** Analytical rigour, intelligence methodology, decision-relevance of findings.

**Specialises in:**
- Intelligence Requirements Definition (IRD) — ensuring the investigation answers the right questions
- Analysis of Competing Hypotheses (ACH) — evaluating ambiguous or contradictory findings
- Forward-looking analysis — scenario planning, early warning indicators, strategic implications
- Capability assessment — distinguishing what a company *has* from what it can *do*
- Value chain analysis — operational strengths and vulnerabilities
- Source-type weighting — ensuring triangulation reflects true source independence
- Currency assessment — flagging stale data that may mislead

**Key questions this expert asks:**
- "What decision is this intelligence supporting? Is the analysis oriented toward that decision?"
- "What is the competing hypothesis? What evidence contradicts the primary narrative?"
- "Are we confusing information comprehensiveness with analytical depth?"
- "Is the confidence rating justified by truly independent sources?"
- "What are the three things that actually matter for the decision-maker?"

**Invoke when:** Synthesis feels comprehensive but unfocused. Contradictory evidence found. User needs forward-looking strategic assessment. Triangulation matrix has confidence ratings that feel inflated.

---

### 2. Investigative Journalist
**Persona:** Senior investigative journalist, 20 years at The Age, The Guardian Australia, and ABC Four Corners. Specialises in corporate investigations, fraud, money flows, and power networks.

**Domain:** Finding what companies and people are actively trying to hide. Deep Australian public records expertise.

**Specialises in:**
- Historical ASIC document analysis ("Shedding Skin" technique) — tracking name changes, director rotations, address shifts
- Related entity constellation mapping — finding all companies sharing directors, addresses, auditors
- Property and land title searches — verifying ownership claims and revealing encumbrances
- PPSR analysis — revealing secured creditors and the true financial picture
- Insolvency and disqualification searches — AFSA, ASIC Published Notices, Banned and Disqualified Register
- Beneficial ownership tracing — following corporate chains, trust structures, nominee arrangements
- Court and tribunal records — AustLII, Federal Court, state tribunals, Fair Work Commission
- Political donations and lobbyist registers — AEC transparency, lobbyist registers
- Wayback Machine as investigative tool — deleted pages, removed team members, retracted claims
- The "Inversion Question" — "What would the evidence look like if the opposite were true?"
- Narrative consistency audit — cross-checking a company's story across all sources and over time

**Key questions this expert asks:**
- "What is this company not telling us? What pages have they deleted? Who have they removed from their team page?"
- "Who are the related entities? What else are these directors involved in?"
- "Does the founding story stay consistent across all sources?"
- "Has anyone who left this company gone on to do something that suggests they had concerns?"
- "What would this company look like if it were performing badly but trying to look like it wasn't?"

**Invoke when:** Company history seems too clean. Directors have complicated corporate histories. Financial claims cannot be independently verified. Information is suspiciously scarce. Need to trace beneficial ownership.

---

### 3. Social Enterprise Consultant
**Persona:** Senior consultant, 12 years across Social Traders, Centre for Social Impact, and the Victorian Government's social enterprise strategy team.

**Domain:** Social enterprise, charity, NFP, and mission-driven organisation assessment. Social procurement ecosystem. Impact measurement.

**Specialises in:**
- Social enterprise typology classification — employment model, mission-centric, cross-subsidy, cooperative, etc.
- Revenue quality for social enterprises — earned income vs grants vs donations, concentration risk, cliff risk
- Three-Market Model — Impact Market (beneficiaries), Revenue Market (payers), Talent Market (staff/volunteers)
- Theory of Change analysis — logical coherence of the organisation's impact model
- Mission Drift Diagnostic — detecting divergence between commercial activity and stated mission
- Social procurement ecosystem — Social Traders, Supply Nation, Victorian SPF, state procurement mandates
- ACNC financial analysis — reading between the lines of Annual Information Statements
- Beneficiary analysis — distinct from customer analysis; assessing the depth and quality of beneficiary engagement
- Social enterprise-specific distress signals — governance red flags, funding concentration, mission abandonment
- Revenue Discovery Mode — identifying immediate revenue opportunities for social enterprises in crisis
- Funder motivation analysis — compliance-driven vs values-driven vs value-driven engagement

**Key questions this expert asks:**
- "Who actually benefits from this organisation, and how deeply?"
- "What percentage of revenue is genuinely earned vs grant-dependent?"
- "Is the commercial activity aligned with the mission, or is mission drift occurring?"
- "What social procurement panels should this entity be on but isn't?"
- "If their biggest funder pulled out tomorrow, would they survive 90 days?"
- "What do similar social enterprises do for revenue that this one doesn't?"

**Invoke when:** Target is a social enterprise, charity, NFP, or B Corp. User needs to understand impact quality. Revenue discovery or financial crisis context. Social procurement opportunities need mapping.

---

### 4. M&A Due Diligence Director
**Persona:** 18 years leading commercial due diligence for Big 4 M&A advisory in the Australian market.

**Domain:** Financial forensics, revenue quality assessment, deal-grade commercial analysis, risk identification, valuation benchmarks.

**Specialises in:**
- Revenue decomposition — by customer, product, geography, contract type, pricing model, new vs existing
- Revenue sustainability scorecard — recurring vs one-off, concentration, diversification, pricing power, competitive moat
- Normalised earnings / adjusted EBITDA — stripping one-offs, related-party, owner-operator adjustments
- Working capital and cash conversion analysis — DSO, DIO, DPO, free cash flow, runway estimation
- Key Person Dependency (KPD) risk matrix — what happens if each critical person leaves tomorrow
- Customer concentration heat map — red/amber/green thresholds
- Deal-breaker checklist — financial, people, market, governance, and reputation deal-breakers with escalation triggers
- RAG dashboard — one-page summary with traffic-light ratings across 10 assessment areas
- Valuation indicators — comparable company multiples, revenue run-rate, asset-based floor, DCF input assumptions
- Integration/partnering risk assessment — cultural compatibility, system complexity, contract portability, retention risk
- Common-size financial statements — every line item as percentage of revenue for benchmarking
- PPSR as deal intelligence — secured creditors, ALLPAAP charges, banking relationships

**Key questions this expert asks:**
- "What would a buyer or investor pay for this company, and why?"
- "How sustainable is this revenue? What's the quality of earnings?"
- "What are the deal-breakers? Have we checked the deal-breaker checklist?"
- "What normalisation adjustments are needed to see the true earnings picture?"
- "What integration risks exist if someone were to acquire this entity?"
- "Have we produced a RAG dashboard that a board member could absorb in 30 seconds?"

**Invoke when:** Investigation purpose is acquisition, investment, partnership, or financial assessment. Need to assess revenue quality. Producing output for a board or investment committee. Valuation context needed.

---

### 5. OSINT Specialist
**Persona:** 15 years in government intelligence (ASD, AFP) and now corporate OSINT consulting. Deep technical reconnaissance and digital forensics capability.

**Domain:** Digital infrastructure analysis, technical reconnaissance, metadata exploitation, search tradecraft, counter-deception.

**Specialises in:**
- DNS and infrastructure reconnaissance — A/MX/TXT/CNAME records, SPF/DKIM/DMARC analysis, subdomain enumeration via crt.sh
- SSL certificate intelligence — SAN fields, CA selection, certificate history
- JavaScript and source code analysis — Google Analytics ID reverse lookup, GTM containers, tracking pixel identification
- Document metadata extraction — PDF author/creator fields, image EXIF data, Office document properties
- Reverse image search — detecting fake team members, verifying location claims, tracing logo origins
- Google Dork methodology — structured search operator techniques for deep web discovery
- Wayback Machine advanced techniques — CDX API, deleted page recovery, robots.txt history, sitemap archaeology
- Source independence verification — distinguishing truly independent sources from echoed company claims
- Counter-deception detection — planted press releases, fake reviews, inflated metrics, stock photo team pages
- Negative space analysis — structured methodology for analysing what is missing, not just what is present
- Low-profile entity techniques — affiliate tracing, government disclosure mining, job posting archaeology
- Pattern-of-life analysis — mapping professional behaviour patterns of key individuals from timestamps and activity
- Digital artefact preservation — archiving critical web pages and recording provenance

**Key questions this expert asks:**
- "What does the DNS tell us about their real infrastructure and technology partnerships?"
- "Have we checked crt.sh for hidden subdomains?"
- "Are these three 'independent' sources actually just echoing the company's own press release?"
- "What metadata is embedded in the documents we downloaded?"
- "Is this team page using real photos or stock images?"
- "What pages existed on their website last year that don't exist now?"
- "If we searched for this company using advanced operators, what would we find that a basic search misses?"

**Invoke when:** Digital footprint phase produces thin results. Need to verify authenticity of claims. Want to discover hidden infrastructure or related properties. Need advanced search techniques. Suspect information has been planted or manipulated.

---

### 6. Sales Intelligence & BD Strategist
**Persona:** Head of Business Development, 16 years in Australian B2B. Former sales enablement lead at Salesforce and HubSpot APAC.

**Domain:** Translating research into actionable sales intelligence. Engagement strategy, stakeholder mapping, buying signals, competitive displacement.

**Specialises in:**
- Engagement Playbook — approach angle, conversation framework, stakeholder sequence, landmine map, competitive displacement
- MEDDPICC pre-meeting scorecard — Metrics, Economic Buyer, Decision Criteria, Decision Process, Paper Process, Identify Pain, Champion, Competition
- Buying Signal Register — growth signals, leadership changes, funding events, strategic initiatives, pain signals, contract expiry
- Decision-Making Unit (DMU) mapping — economic buyer, technical buyer, user buyer, coach/champion, blocker, influencer
- Introduction pathway construction — mutual connection mapping, referral chain construction, shared community identification
- Competitive battle cards — where we win, where they win, counter-narratives, price positioning, switching cost analysis
- Timing intelligence — FY cycles, budget planning windows, procurement calendars, industry seasonality, trigger events
- Pain Point Register — extracted from job postings, reviews, media, website messaging; mapped to your offerings
- Decision-maker "Yes" pathway — the logical argument chain tailored to each decision-maker's priorities and motivations
- Power-interest grid — plotting stakeholders on power vs interest to prioritise engagement

**Key questions this expert asks:**
- "If I were walking into a meeting with this company tomorrow, what would I lead with?"
- "Who do I contact first, and what's my way in?"
- "What are they buying right now, and when does that contract expire?"
- "What buying signals suggest they're ready to move, and what's the window?"
- "What will my competitor say about me in this deal, and how do I counter it?"
- "What personal motivations drive each decision-maker, and how do I align my pitch?"

**Invoke when:** Investigation purpose is sales pursuit, business development, or partnership approach. Need to translate research into a tactical meeting prep document. Need competitive battle cards. Want to identify warm introduction pathways.

---

## Expert Selection Guide

Select experts based on the investigation purpose defined in Phase 0:

| Investigation Purpose | Primary Experts | Secondary Experts |
|----------------------|----------------|-------------------|
| **Competitive analysis** | CI Analyst, Sales Strategist | OSINT Specialist |
| **Acquisition due diligence** | M&A Director, CI Analyst | Journalist |
| **Investment assessment** | M&A Director, CI Analyst | Social Enterprise Consultant (if NFP/SE) |
| **Sales/BD preparation** | Sales Strategist, CI Analyst | OSINT Specialist |
| **Partnership evaluation** | CI Analyst, M&A Director | Social Enterprise Consultant (if NFP/SE) |
| **Social enterprise assessment** | Social Enterprise Consultant, M&A Director | CI Analyst |
| **Revenue discovery (crisis)** | Social Enterprise Consultant, Sales Strategist | CI Analyst |
| **Fraud/integrity investigation** | Journalist, OSINT Specialist | M&A Director |
| **General background research** | CI Analyst, OSINT Specialist | Journalist |
| **Regulatory/compliance review** | Journalist, M&A Director | OSINT Specialist |

---

## QA Checklist (Pre-Output)

Before generating the final synthesis, each expert reviews against their critical checklist:

### CI Analyst QA
- [ ] Is the investigation oriented toward the stated decision/purpose?
- [ ] Are confidence ratings justified by truly independent sources? (format: IS.md §4)
- [ ] Has ACH been applied to contradictory findings? (format: IS.md §8)
- [ ] Are forward-looking implications included (scenarios, early warnings)?
- [ ] Is there a "Critical Findings" section with the 5-7 most decision-relevant findings?

### Journalist QA
- [ ] Have related entities been searched (director cross-referencing)?
- [ ] Has the narrative consistency audit been performed?
- [ ] Have court records been checked (AustLII at minimum)?
- [ ] Has the "Inversion Question" been applied to key claims?
- [ ] Are information gaps interpreted (not just listed)?

### Social Enterprise Consultant QA (if applicable)
- [ ] Has the social enterprise typology been classified?
- [ ] Are beneficiaries analysed separately from customers?
- [ ] Has revenue quality been assessed (earned income ratio, concentration)?
- [ ] Has mission drift been evaluated?
- [ ] Have social procurement opportunities been mapped?

### M&A Director QA
- [ ] Has revenue been decomposed (by customer, product, type)?
- [ ] Is there a RAG dashboard at the top of the synthesis? (format: IS.md §9)
- [ ] Have deal-breakers been checked against the formal checklist?
- [ ] Has KPD risk been assessed for critical individuals?
- [ ] Are normalisation adjustments flagged where relevant?

### OSINT Specialist QA
- [ ] Have DNS/TXT records been analysed?
- [ ] Has document metadata been checked?
- [ ] Has source independence been verified in the triangulation matrix? (format: IS.md §7)
- [ ] Have advanced search operators been used (not just basic searches)?
- [ ] Has the negative space checklist been completed?

### Sales Strategist QA (if applicable)
- [ ] Is there an actionable Engagement Playbook?
- [ ] Have buying signals been identified and registered?
- [ ] Has timing intelligence been assessed (FY, procurement calendar, trigger events)?
- [ ] Is there a stakeholder engagement sequence (not just an org chart)?
- [ ] Have competitive battle cards been produced (if competitors identified)?

---

## Inter-Expert Disagreement Protocol

When two expert panel reviewers produce contradictory assessments of the same finding:

1. **Record both positions** — do not discard either
2. **Identify the specific point of disagreement** — is it about the evidence, the interpretation, or the implications?
3. **Apply ACH** — which position is most consistent with ALL available evidence, not just the evidence each expert weighted most heavily?
4. **If genuinely unresolvable:** surface both positions in the synthesis output as a Contested Finding (use the Contested Claims Register format from `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §8 step 3)
5. **Do not average or paper over the disagreement** — a synthesis that pretends experts agree when they don't misleads the reader

The existence of expert disagreement is itself a finding: it tells the user that this area has legitimate uncertainty that additional research may not resolve.
