# company-intel skill

Deep background research and competitive intelligence on any named company or organisation.

## What it researches

Companies, private SMEs, ASX-listed companies, PE-backed businesses, NFPs/charities, social enterprises, government agencies, statutory bodies, and foreign subsidiaries operating in Australia.

## Seven entity-type modules

| Code | Type | Source priority |
|---|---|---|
| STA | Startup / early-stage | Crunchbase, LinkedIn, Product Hunt, VC portfolios |
| SME | Private SME | ASIC, PPSR, AusTender, Glassdoor, AustLII |
| ASX | ASX-listed company | ASX announcements, annual reports, analyst data |
| PEQ | PE-backed / VC-backed | PitchBook, ASIC structure, PE firm portfolios |
| NFP | NFP / charity / social enterprise | ACNC, GrantConnect, Social Traders, AusTender |
| GOV | Government agency | Legislation, Portfolio Budget Statements, ANAO, Hansard |
| FOR | Foreign subsidiary | Parent filings, ASIC foreign company, FIRB |

## v1.0.0 — Anti-Hallucination Protocol

- **Cite-Before-You-Write** — every synthesis claim mapped to a source file before prose is written
- **Numeric Quarantine** — every number verified against its source file before PDF generation
- **Fabrication Detection Pass** — 12-flag checklist plus 5 company-intel-specific risk patterns
- **Privacy Compliance Checkpoint** — Privacy Act 1988 (Cth) obligations surfaced before data aggregation begins
- **Data-Currency Warnings** — ASIC/ACNC registry lag flagged per entity type
- **Adversarial Search** — counter-hypothesis queries run before synthesis to surface unknown risks

## Install

```bash
npx skills add thedanielmay/company-intel-skill
```

## Features

- 11 research phases: Identification, Website, News/Media, LinkedIn, Financial/Legal, People Profiling, Reputation, Digital Footprint, Customers/Stakeholders, Industry/Market, Synthesis
- Four investigation tiers: Quick Scan, Standard, Full Investigation, Revenue Discovery
- Five-wave parallel research execution with agent dispatch templates (Agents A-K)
- Entity-type expert panels (3 experts x 7 entity types) with 3 integration modes
- Australian-specific sources: ASIC, ACNC, PPSR, AusTender, AustLII, ABR, Fair Work Commission
- PDF synthesis report with timestamped filename
- Refresh Investigation protocol with contradiction tracking
- Shared standards with topic-intel via `INTELLIGENCE-STANDARDS.md`
