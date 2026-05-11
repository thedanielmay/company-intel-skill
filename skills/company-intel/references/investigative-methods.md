# Investigative Methods Reference

Reference document for advanced investigative journalism and due diligence techniques used within the company-intel skill. These methods are activated during **Phase 5 (Financial & Legal)**, **Phase 6 (People)**, and whenever standard research produces thin or suspicious results.

Each technique explains **what** it is, **why** it matters, and **how** to execute it.

---

## Phase-Technique Quick Reference

Use this table to identify which techniques are most relevant for each investigation phase:

| Phase | Primary techniques | Secondary techniques |
|---|---|---|
| Phase 0 — Scoping | Subject disambiguation, OSINT pre-check | — |
| Phase 1 — Foundation | Corporate register search, ABR lookup | ASIC extract |
| Phase 2 — Financials | ACNC financial extraction, ratio analysis | Glassdoor (headcount proxy) |
| Phase 3 — People | LinkedIn protocol (Layer 4), AEC donations search | Media archive search |
| Phase 4 — Commercial | Web presence analysis, job posting analysis | TXT record OSINT |
| Phase 5 — Market | Competitor profiling, market sizing via ABS | AusTender/GrantConnect |
| Phase 6 — Reputation | Media timeline construction, Glassdoor analysis | Court record search (AustLII) |
| Phase 7 — Network | Stakeholder mapping, relationship graph | Political donations register |
| Phase 8 — Digital | DNS/infrastructure OSINT, tech stack analysis | Meta Ad Library |
| Phase 9 — Risk | Adverse media synthesis, regulatory breach search | AFCA/EDR scheme records |
| Phase 10 — Industry | Sector analysis frameworks, government spend analysis | topic-intel hand-off |
| Phase 11 — Synthesis | Triangulation Matrix, Narrative Consistency Audit | ACH, Devil's Advocate |

For Layer 4 (Playwright) techniques, see `layer-4-playwright-protocol.md`.

---

## 1. Historical Corporate Structure Analysis ("Shedding Skin" Technique)

**What it is:**
A longitudinal analysis of a company's full ASIC document history — not the current snapshot, but the complete record of every structural change since incorporation. This tracks director appointments and resignations, share transfers and allotments, company name changes, registered office address changes, principal place of business changes, and company secretary appointments/changes.

**Why it matters:**
Companies that undergo frequent structural changes are often signalling instability, avoidance behaviour, or deliberate obfuscation. A company that changes its name 3+ times in 5 years and cycles through numerous directors is often shedding a problematic history. Each name change makes historical research harder — media articles, court records, and complaints reference the old name. This is sometimes deliberate. Cross-referencing the dates of structural changes with external negative events (media coverage, court filings, regulatory action) often reveals a pattern: negative event occurs, then within weeks the company changes name, replaces directors, or shifts its registered address.

**How to execute it:**
1. Pull the full ASIC company extract (historical, not current) via the company's ACN.
2. Build a chronological timeline of every document lodged, capturing:
   - All Form 484 (Change to Company Details) filings — note exact dates and what changed.
   - All Form 370 (Notification of Resolution) filings — name changes, constitutional changes.
   - All director and secretary appointment/cessation dates.
   - All share transfer and allotment dates.
3. On a parallel timeline, map external events: media articles, court filings, regulatory notices, PPSR registrations.
4. Look for temporal correlations — structural changes clustering around negative events.
5. Calculate the "churn rate" — number of unique directors divided by years of operation. A ratio above 1.5 is noteworthy; above 3.0 is a significant signal.
6. Note the velocity of name changes. One name change in a company's life is normal. Three or more in five years is a pattern worth investigating.

---

## 2. Related Entity Constellation Mapping

**What it is:**
A systematic mapping of every company connected to the subject company through shared directors, secretaries, registered addresses, or auditors. For every individual identified in the company's structure, this technique searches ASIC for all other entities where they hold or have held directorships, producing a complete corporate "constellation."

**Why it matters:**
A company does not exist in isolation. The full network of related entities reveals the true scope and pattern of the principals' activities. A director with a trail of deregistered or externally administered companies is a fundamentally different risk profile from one whose related entities are all active and compliant. Shared registered addresses, company secretaries, and auditors reveal operational connections that may not be disclosed. The "Common Address" signal — a suburban residential house listed as the registered office for seven different companies — is a notable indicator of either a home-based operator (not inherently negative but relevant to scale claims) or a shell company network.

**How to execute it:**
1. List every current and former director, secretary, and shareholder identified in the subject company's ASIC extract.
2. For each individual, search ASIC's registers for all other companies where they appear as director, secretary, or shareholder.
3. For each related entity found, record:
   - Company name and ACN
   - Individual's role and dates
   - Current company status (registered, deregistered, under external administration, struck off)
   - Registered office address
   - Company secretary and auditor names
4. Map the full constellation visually or in a structured table.
5. Identify shared nodes: same registered address across multiple entities, same company secretary, same auditor.
6. Check the status of every related entity. Calculate the ratio of deregistered/failed entities to active ones.
7. Note any entities with similar names or operating in similar sectors — these may indicate serial business attempts in the same space.
8. Document the full corporate family tree, distinguishing between currently active relationships and historical ones.

---

## 3. Beneficial Ownership Tracing

**What it is:**
An attempt to determine who truly owns and controls a company, looking beyond the names on ASIC filings to trace the chain of ownership through corporate shareholders, trust structures, and nominee arrangements.

**Why it matters:**
Australia currently lacks a public beneficial ownership register. This means the legal owners shown on ASIC records may not be the people who ultimately control or benefit from the company. Corporate structures are legitimately used for asset protection and tax planning, but they also enable concealment of control. Understanding true beneficial ownership is essential for assessing conflicts of interest, related-party risks, and the alignment of incentives between controllers and stakeholders.

**How to execute it:**
1. **Corporate shareholders:** When a company's shares are held by another company (Company B owns Company A), trace upward. Pull Company B's ASIC extract and identify its shareholders. Continue tracing until you reach natural persons or reach a dead end (offshore entity, trust).
2. **Trust structures:** When a company name includes "as Trustee for the XYZ Trust" (e.g., "ABC Pty Ltd as Trustee for the XYZ Trust"), recognise that:
   - The company (ABC Pty Ltd) is the legal entity, but the trust is the economic entity.
   - Trust deeds and beneficiary information are not publicly filed in Australia.
   - The directors of the trustee company control the trust assets.
   - Beneficiaries of the trust (who ultimately receive distributions) are not publicly disclosed.
3. **Nominee director arrangements:** When a director appears to be a professional nominee (e.g., from an accounting or legal firm), flag that the true decision-maker may be someone else. Look for patterns: nominee directors from the same firm across multiple related entities.
4. **Flag opacity:** When the ownership chain cannot be traced to natural persons through public records, explicitly state this as an information gap. Note where the chain breaks (offshore holding company, trust structure, nominee arrangement) and what this means for the analysis.
5. **Cross-reference control indicators:** Even when legal ownership is opaque, control may be evident from other signals — who signs contracts, who appears in media, who speaks at industry events, who is listed on the website as leadership.

---

## 4. Property and Land Title Searches

**What it is:**
Searches of state-based land title registries to identify property ownership, encumbrances, mortgages, and transaction history linked to a company or its directors.

**Why it matters:**
Property records reveal information that corporate filings do not: the real assets backing a business, the extent of secured debt, personal guarantees by directors, and the timing of property transactions relative to business events. A director purchasing property immediately before a company enters administration, or a company mortgaging its property to multiple lenders, tells a story that financial statements alone cannot.

**How to execute it:**
1. **Identify relevant registries by state:**
   - **VIC:** Landata (landata.vic.gov.au)
   - **NSW:** NSW Land Registry Services (nswlrs.com.au)
   - **QLD:** Titles Queensland Registry
   - **SA:** SAILIS (South Australian Integrated Land Information System)
   - **WA:** Landgate (landgate.wa.gov.au)
   - **TAS:** Land Information System Tasmania (LIST)
   - **ACT:** ACT Land Titles
   - **NT:** Land Titles Office NT
2. **Search by company name and ACN** for properties held directly by the company.
3. **Search by director names** for properties held personally — relevant for assessing personal financial position and identifying personal guarantees.
4. **For each property found, note:**
   - Current registered owner(s)
   - Mortgages and the identity of mortgagees (lenders)
   - Caveats (third-party claims on the property)
   - Encumbrances and covenants
   - Historical transfers and transaction prices
   - Dates of all transactions
5. **Cross-reference** property acquisition dates with company financial events. Property purchases during periods of financial distress, or mortgages taken out shortly before administration, are significant.
6. **Check mortgage documents** where available — they may reveal personal guarantees by directors for company debts, the quantum of secured debt, and the identity of primary lenders.

---

## 5. PPSR (Personal Property Securities Register) Analysis

**What it is:**
A search of the Personal Property Securities Register (ppsr.gov.au) against a company's ABN or ACN to identify all registered security interests over the company's personal property (everything that is not land).

**Why it matters:**
The PPSR reveals the hidden debt structure of a company. While financial statements show liabilities in aggregate, PPSR registrations identify specific creditors, the nature of their security, and the extent of their claims. This is one of the most underused public intelligence sources in Australian corporate research.

**How to execute it:**
1. Search ppsr.gov.au using the company's ABN and/or ACN.
2. For each registration found, record:
   - **Secured party** (the creditor) — who has taken security
   - **Collateral class** — what property is secured (equipment, inventory, accounts receivable, intellectual property, or "all present and after-acquired property" [ALLPAAP])
   - **Registration date and duration** — when the security was granted and how long it runs
   - **Serial number details** — for specific equipment/vehicles
3. **Interpret the findings:**
   - **ALLPAAP charge** (All Present and After-Acquired Property): A blanket security interest over everything the company owns. Typically held by the primary banker. This creditor ranks first in any insolvency.
   - **Multiple PPSR registrations from different financiers:** Suggests the company is heavily leveraged and has borrowed from multiple sources, each taking security over different assets.
   - **Single creditor with blanket security:** Reveals the primary banking relationship and suggests a more conventional lending structure.
   - **Equipment leases and hire-purchase agreements:** Visible as PPSR registrations. High numbers suggest the company does not own its operating equipment outright.
   - **ATO as a secured creditor:** The Australian Taxation Office registering on the PPSR is a significant signal — it typically means the company has a tax debt and the ATO is protecting its position. This is a potential deal-breaker signal.
4. **Timeline analysis:** Plot registration dates chronologically. A cluster of new registrations in a short period may indicate a company taking on significant new debt. Registrations that have expired and not been renewed may indicate debt has been repaid or the relationship has ended.

---

## 6. Insolvency and Disqualification Searches

**What it is:**
A set of targeted searches across Australian regulatory databases to identify whether the company or its directors have been subject to insolvency proceedings, personal bankruptcy, or regulatory disqualification.

**Why it matters:**
These are hard signals. A director who has been personally bankrupt, a company that has been through external administration, or an individual who has been banned from managing corporations — these are not matters of interpretation. They are facts that fundamentally affect risk assessment. They are also facts that subjects rarely volunteer.

**How to execute it:**

### ASIC Published Notices
- Search ASIC's published notices (search.asic.gov.au) for the company name and ACN.
- Look for: external administration appointments (voluntary administration, receivership, liquidation), winding-up applications, controller appointments, deregistration notices.
- Check the dates — a company that was previously in voluntary administration and has since been returned to the directors' control has a significantly different history from one that has never faced administration.

### AFSA National Personal Insolvency Index (NPII)
- Search the National Personal Insolvency Index (afsa.gov.au) for each director by name and date of birth (if available).
- The NPII records: bankruptcy, debt agreements (Part IX), personal insolvency agreements (Part X).
- A director with a personal insolvency history is not automatically disqualified from holding office (depending on timing and type), but it is a material fact for risk assessment.

### ASIC Banned and Disqualified Register
- Search ASIC's register of banned and disqualified persons for every director identified.
- This register includes individuals who have been: disqualified from managing corporations (under the Corporations Act), banned from providing financial services, banned from engaging in credit activities.
- A current disqualification while holding a directorship is a legal violation and an immediate deal-breaker.

### AUSTRAC Public Enforcement Actions
- Check the Australian Transaction Reports and Analysis Centre (AUSTRAC) for any public enforcement actions against the company.
- AUSTRAC enforces anti-money laundering and counter-terrorism financing obligations. Enforcement actions indicate serious compliance failures.

---

## 7. Court and Tribunal Search Guide

**What it is:**
A structured guide to searching Australian courts and tribunals for litigation involving a company or its directors, covering all major jurisdictions and tribunals.

**Why it matters:**
Litigation history reveals disputes, regulatory enforcement, contractual failures, employment issues, and commercial conflicts that do not appear in any other public source. A company with no litigation is not necessarily clean — it may simply be small or have settled disputes privately. But a company with a pattern of litigation (especially as defendant) across multiple jurisdictions reveals systemic issues.

**How to execute it:**

### AustLII (austlii.edu.au)
The PRIMARY free legal research tool. Covers all Australian jurisdictions. Search by company name AND by each director's name. Use quotation marks for exact phrase matching. Check multiple name variations (including former company names identified in Phase 1). AustLII indexes: High Court, Federal Court, Family Court, all State and Territory Supreme Courts, many lower courts and tribunals.

### Federal Court of Australia
- Judgments: judgments.fedcourt.gov.au
- Daily court lists available online.
- Covers: corporations law disputes, intellectual property, competition law, consumer law, migration, tax appeals, bankruptcy.

### High Court of Australia
- eresources.hcourt.gov.au
- Only matters of national legal significance reach here. If the company appears in High Court records, it is involved in a significant legal matter.

### Administrative Appeals Tribunal / Administrative Review Tribunal (AAT/ART)
- Covers tax disputes (challenges to ATO assessments), migration decisions, FOI decisions, social services decisions.
- Tax disputes are particularly relevant — a company challenging an ATO assessment may have significant tax compliance issues.

### Fair Work Commission
- Covers unfair dismissal claims, enterprise bargaining, industrial disputes.
- Multiple unfair dismissal claims from different employees suggest systemic employment practice issues.
- Published decisions searchable online.

### ACCC Enforcement Register
- The Australian Competition and Consumer Commission publishes: court enforceable undertakings, infringement notices, court actions.
- Check both the company name and the industry/sector.
- An enforceable undertaking means the ACCC identified a breach and the company agreed to specific remedial actions without court proceedings.

### State Supreme Courts
- Each state's Supreme Court decisions are indexed on AustLII.
- Covers major commercial disputes, insolvency matters, injunctions, contractual disputes.

### State Tribunals
- **VCAT** (Victorian Civil and Administrative Tribunal) — consumer disputes, building disputes, planning, civil claims.
- **NCAT** (NSW Civil and Administrative Tribunal) — equivalent jurisdiction to VCAT.
- **QCAT** (Queensland Civil and Administrative Tribunal) — equivalent jurisdiction.
- These tribunals handle high volumes of consumer and building disputes. Multiple appearances as respondent in consumer disputes is a significant operational signal.

### State Magistrates Courts
- Lower-value civil claims, minor criminal matters.
- Less consistently indexed online. May require direct registry searches.

---

## 8. Political Donations and Lobbying

**What it is:**
Research into a company's political donation history, lobbying registrations, and relationships with government decision-makers.

**Why it matters:**
Political donations and lobbying activity reveal a company's power networks, political alignment, and strategies for influencing government decisions. For companies that depend on government contracts, grants, or regulatory approvals, these connections are material to understanding business sustainability and risk. Donation patterns that align with contract awards or regulatory decisions are particularly noteworthy.

**How to execute it:**

### AEC Transparency Register
- Search the Australian Electoral Commission's transparency register (transparency.aec.gov.au) by company name AND by each director's name individually.
- Donations above the disclosure threshold are publicly reported. Search across multiple financial years to identify patterns.
- Note: donations may be made through related entities or personally by directors — searching both company and individual names is essential.

### Australian Government Register of Lobbyists
- Search lobbyistsregister.gov.au for the company name and for any third-party lobbying firms acting on its behalf.
- The register shows: who is lobbying, on whose behalf, and which government departments/agencies they are authorised to lobby.

### State Lobbyist Registers
- Victorian Register of Lobbyists
- NSW Lobbying Register
- QLD Lobbyist Register
- Other state equivalents
- Companies may lobby at state level even if not registered federally, particularly for state-regulated industries (planning, resources, health, education).

### Interpreting donation patterns
- Donations to both major parties suggest pragmatic relationship-building rather than ideological alignment.
- Donations concentrated on one party, especially around election periods, suggest a strategic bet on that party's success.
- Donations that spike before or after major government decisions affecting the company are noteworthy.
- Director personal donations may reveal political networks not visible through company-level analysis.

---

## 9. Parliamentary Records (Hansard)

**What it is:**
A search of Australia's parliamentary records — the official transcripts of everything said in Parliament, Senate, and parliamentary committees — for references to the company, its directors, or its sector.

**Why it matters:**
Parliamentary records are free, comprehensive, and searchable. They capture Senate Estimates hearings (where public servants are questioned about government spending), parliamentary inquiries (detailed investigations into specific sectors or issues), and Questions on Notice (written questions from parliamentarians targeting specific companies or programs). For companies in government-heavy sectors — defence, infrastructure, social services, aged care, NDIS, education, health — parliamentary records can reveal information available nowhere else: contract values, performance concerns, policy changes, and political scrutiny.

**How to execute it:**

### ParlInfo Search (parlinfo.aph.gov.au)
- Search by company name, including former names and trading names.
- Search by director names, especially for senior figures who may have appeared as witnesses.
- Filter by document type to focus on the most relevant sources.

### Senate Estimates Hearings
- The most valuable source. Government departments are questioned in detail about their spending and contracts. If the company received government funding, procurement contracts, or grants, the details may have been discussed during Estimates.
- Search within specific portfolio estimates (e.g., Defence estimates for a defence contractor, Social Services estimates for an NDIS provider).

### Parliamentary Inquiries and Committee Reports
- Senate and House committees conduct inquiries into specific sectors and issues. Companies may appear as witnesses (positive — invited to contribute expertise) or as subjects of concern (negative — raised as examples of problems).
- Final committee reports contain findings and recommendations that may directly affect the company's operating environment.

### Questions on Notice
- Written questions from parliamentarians to ministers. These are targeted and specific. A Question on Notice about a particular company indicates that a parliamentarian has received information (often from a constituent, whistleblower, or competitor) prompting formal inquiry.
- The minister's written response often contains detailed factual information not available elsewhere.

### Particularly Valuable For
- Defence and national security contractors
- Infrastructure and construction companies with government contracts
- Social services providers (aged care, disability, child protection)
- NDIS registered providers
- Education providers (especially those receiving government funding)
- Health services with government contracts or Medicare reliance
- Companies receiving significant government grants or subsidies

---

## 10. The "Inversion Question"

**What it is:**
A core investigative technique: take the company's most prominent positive claim and systematically ask "What would the evidence look like if the OPPOSITE were true?" Then search for that counter-evidence.

**Why it matters:**
Confirmation bias is the greatest enemy of due diligence. Researchers naturally seek evidence that confirms what they have been told. The Inversion Question forces the opposite approach — deliberately searching for disconfirming evidence. If you search for evidence that the company is failing and find none, your positive assessment is strengthened. If you find compelling counter-evidence, you have identified a critical gap between narrative and reality. If you cannot distinguish between positive and negative interpretation — if the evidence is genuinely ambiguous — you have identified a significant information gap that must be explicitly flagged.

**How to execute it:**

### Apply to financial claims
- **Claim:** "We are growing rapidly."
- **Inversion:** What would evidence of stagnation or decline look like? Check: Are they hiring or reducing headcount? Are job postings increasing or decreasing? Are they expanding to new markets or consolidating? Are they taking on more debt (PPSR registrations increasing)? Are payment terms extending?

### Apply to impact claims
- **Claim:** "We have transformed outcomes for 10,000 beneficiaries."
- **Inversion:** What would evidence of no impact look like? Check: Are there independent evaluations? Do beneficiary testimonials come from verifiable sources? Do government reports on the program mention measurable outcomes? Are comparable programs reporting similar numbers?

### Apply to partnership claims
- **Claim:** "We work with [Major Organisation]."
- **Inversion:** What would evidence of no real partnership look like? Check: Does the partner's website mention them? Is the "partnership" actually just a vendor/customer relationship? Is it a one-off project being characterised as an ongoing partnership? Has the partner confirmed the relationship publicly?

### Apply to growth narrative
- **Claim:** "We are expanding into three new markets."
- **Inversion:** What would evidence of contraction look like? Check: Are they closing offices? Have they withdrawn from any markets? Are key staff in "new markets" actually based at headquarters? Are there job postings for the new markets?

### Apply to team stability narrative
- **Claim:** "We have an experienced, stable leadership team."
- **Inversion:** What would evidence of instability look like? Check: LinkedIn departure patterns. ASIC director cessation dates. Glassdoor reviews mentioning leadership turnover. Absence of key people from recent public appearances who were previously prominent.

---

## 11. Narrative Consistency Audit

**What it is:**
A systematic comparison of the company's story across ALL available sources and over time, checking for contradictions, inconsistencies, unexplained changes, and gaps between claims and observable evidence.

**Why it matters:**
Genuine companies tell a consistent story because it is true. Their founding date matches ASIC records, their employee count matches LinkedIn, their revenue figures stay consistent across interviews, and their mission statement does not fundamentally shift every two years. Inconsistencies are not always deliberate deception — they can result from carelessness, aspirational exaggeration, or evolving narrative. But systematic inconsistency across multiple dimensions is a significant signal that warrants deeper investigation.

**How to execute it:**

### Founding story consistency
- Compare the founding narrative told in media interviews, the company website "About" page, and pitch materials against the ASIC incorporation date, the identity of original directors, and the first registered company name.
- Check: Does the claimed founding year match incorporation? Were the claimed founders actually the original directors? Has the founding story evolved to add or remove founding members?

### Numbers consistency
- Compare revenue, employee count, client numbers, and growth rates across all sources where these figures appear: media articles, website claims, LinkedIn company page, ACNC reports (for charities), annual reports, award applications.
- Check: Do the same metric vary by more than 20% across sources from the same time period? Do numbers only go up, or are there occasional honest acknowledgments of setbacks?

### Operational consistency
- Compare descriptions of what the company does across sources: website, LinkedIn, job postings, media articles, client testimonials.
- Check: Do job postings match the company's stated activities? Do LinkedIn employee roles align with claimed capabilities? Do client types match the stated target market?

### Impact claim consistency
- For social enterprises and charities, compare impact claims in media against ACNC Annual Information Statements, annual reports, and independent evaluations.
- Check: Are impact numbers verifiable? Do they match reporting to regulators? Are they measured consistently over time?

### Mission and purpose drift
- Track the company's stated mission, vision, and purpose across its history.
- Check: Has the fundamental purpose shifted without acknowledgment? A company that was "revolutionising education" two years ago and is now "transforming workforce development" may have pivoted — or may be opportunistically chasing funding trends.

---

## 12. Exit Pattern Analysis

**What it is:**
Systematic tracking and analysis of where former employees (especially senior leaders) go after leaving the company, and what their post-departure behaviour reveals about internal conditions.

**Why it matters:**
Current employees are constrained in what they can say. Former employees are not (subject to contractual obligations). Their career moves, public statements, LinkedIn activity, and silence all carry information. Exit patterns are one of the strongest leading indicators of internal health — problems visible through exit patterns often precede public manifestations by 6-18 months.

**How to execute it:**

### Multiple senior departures in short period
- Three or more senior leaders departing within 6 months signals a serious internal problem — strategic disagreement, cultural breakdown, financial distress, or loss of confidence in leadership.
- Check: Did they depart before or after a significant event? Were departures announced or quiet?

### Former employees joining competitors
- Some attrition to competitors is normal in every industry. But systematic recruitment of key staff by a single competitor suggests targeted talent acquisition and may indicate that the competitor is strategically positioning against the company.
- Check: Are the departures from the same team/function? Is the competitor in a growth phase?

### Former employees starting competing businesses
- When former employees start businesses in the same space, they saw an opportunity that the company was not serving, or they believe they can do it better.
- Check: Are former employee startups directly competing or addressing an adjacent niche? Are they taking clients with them?

### Former employees moving to regulators
- A former employee joining a regulatory body (ASIC, ACCC, APRA, a state regulator) may have had compliance concerns that contributed to their departure.
- Check: What role did they hold? Did their departure coincide with any compliance-related events?

### Silence from former leaders
- When a former CEO, founder, or senior leader has completely scrubbed their LinkedIn of references to the company, makes no mention of it in their bio, and does not appear in mutual recommendation networks with current staff — the departure was almost certainly not amicable.
- Check: Do they still list the role? Do they have recommendations from that period? Have mutual connections been severed?

### Recommender Network technique
- LinkedIn recommendations are a curated inner circle — people voluntarily endorse each other. Mapping the recommendation network of key individuals reveals:
  - Who they trust and who trusts them
  - Cross-connections with clients, funders, and board members
  - Gaps where expected recommendations are absent (former colleagues who notably do not endorse each other)
- Cross-reference the recommender network with known clients, funders, board members, and partners. Overlaps reveal relationship depth; absences reveal relationship gaps.
- **Layer 4 required:** See `layer-4-playwright-protocol.md` for LinkedIn authenticated access patterns.

---

## 13. Thin-File Protocol

**What it is:**
A set of specialised investigative techniques activated when standard research channels produce very little information. Some companies are deliberately opaque; others are simply small or new. The Thin-File Protocol uses indirect and unconventional sources to build a picture when direct sources are insufficient.

**Why it matters:**
A thin file is itself a signal. A company that claims significant revenue, numerous clients, and meaningful impact should leave traces across the information ecosystem. When standard research produces very little, the question becomes: is this a small/new company that legitimately has little public footprint, or is this a company that has actively minimised its footprint? The Thin-File Protocol helps distinguish between these two scenarios.

**How to execute it:**

### 1. Supplier and client investigation
- Research who works WITH the company. If the company claims to work with specific organisations, search those organisations' annual reports, media releases, and websites for mentions of the subject company.
- Suppliers, subcontractors, and service providers sometimes reference their clients publicly.

### 2. Industry association membership lists
- Most industry associations publish their member directories. Check whether the company is a member of relevant industry bodies. Absence from all relevant associations is a signal (though not conclusive).

### 3. Government contract disclosures by contracting agencies
- When the company claims government contracts, search from the government side. AusTender (tenders.gov.au) publishes Commonwealth contract awards. State equivalents exist. Local government procurement portals. Search by company name, ABN, and ACN.

### 4. Freedom of Information (FOI) as an option
- FOI requests can compel government agencies to disclose documents about their dealings with a company. The skill cannot lodge FOI requests, but should flag when FOI would be a valuable next step — particularly when:
  - The company receives significant government funding and reporting is not publicly available.
  - Regulatory interactions are suspected but not publicly documented.
  - Government contract performance information would be illuminating.

### 5. Competitor analysis ("Unlike us..." technique)
- Search competitor websites and marketing materials for references to the subject company. Competitors sometimes differentiate themselves by implicit or explicit comparison: "Unlike other providers, we..." or "We were founded in response to..." or direct competitive claims.

### 6. Historical WHOIS records
- Domain registration history can reveal: original registrants, registration dates (useful for verifying founding claims), historical hosting changes, and connections to other domains registered by the same entity.

### 7. Cached and archived content
- Wayback Machine (web.archive.org): historical snapshots of the company's website. Invaluable for tracking how claims, team pages, and client lists have changed over time.
- Google Cache: recent cached versions of pages that may have been modified or removed.

### 8. Overseas corporate registry filings
- If the company claims international operations, check:
  - **NZ:** Companies Office (companies.govt.nz) — free, comprehensive
  - **UK:** Companies House (find-and-update.company-information.service.gov.uk) — free, comprehensive
  - **US:** Relevant state Secretary of State office
  - **Singapore:** ACRA BizFile
  - Inconsistency between Australian claims and overseas filings is a significant signal.

### 9. Google Maps/Street View for registered address
- Check the registered office address and principal place of business on Google Maps and Street View.
- Determine: Is it a real office? A serviced/virtual office? A residential address? A mail-forwarding service?
- Context matters: a startup operating from a home address is different from a company claiming 50 employees operating from a suburban house.

### 10. Job posting archaeology
- Search for historical job postings: site:seek.com.au "company name", site:indeed.com.au "company name", site:linkedin.com "company name" jobs.
- Expired job postings reveal: roles the company was trying to fill (and whether they succeeded), salary ranges offered, required qualifications, and technology stack.
- Postings that remain open for extended periods suggest difficulty attracting talent or, sometimes, postings used for market research rather than genuine recruitment.
- **Layer 4 required:** See `layer-4-playwright-protocol.md` for LinkedIn job page scraping (bot detection applies).

---

## 14. Red Flag Taxonomy

A structured taxonomy of warning signals organised by category. Each flag is not necessarily disqualifying on its own, but accumulation of flags within or across categories significantly elevates risk.

### Corporate Structure Red Flags

| Flag | What It Means |
|------|---------------|
| Frequent name changes (>1 in 5 years) | May be shedding problematic history; makes historical research harder |
| Virtual office / mail forwarding as registered office | Not inherently negative but inconsistent with claims of significant physical operations |
| Late ASIC annual returns | Indicates administrative disorganisation or deliberate avoidance; ASIC charges late fees and can deregister |
| Multiple related entities with similar names | May indicate attempts to separate liabilities or confuse creditors |
| Trust structures behind corporate entities | Legitimate but opaque; beneficiaries unknown; complicates accountability |
| Frequent company secretary changes | Company secretaries handle compliance; frequent changes suggest compliance function instability |

### Financial Red Flags

| Flag | What It Means |
|------|---------------|
| Revenue unverifiable by independent sources | Claims cannot be cross-checked; reliance on self-reporting only |
| Scale claims don't match digital footprint | A company claiming $50M revenue with 5 LinkedIn followers has a credibility gap |
| Charity spending <30% on charitable purposes | ACNC and public expect majority of charity funds directed to purpose; low ratio suggests overhead or governance issues |
| Significant related-party transactions | Money flowing between related entities controlled by the same people; potential for self-dealing |
| Auditor changes mid-year | Auditors rarely leave mid-engagement voluntarily; may indicate disagreement over accounting treatment |
| Qualified audit opinions | Auditor has explicitly flagged issues they could not resolve; always material |
| Overdue/missing ACNC financial reports | Charity is not meeting regulatory obligations; ACNC may be taking compliance action |
| Going concern opinions | Auditor doubts the company can continue operating for 12 months; the most serious audit qualification |

### People Red Flags

| Flag | What It Means |
|------|---------------|
| Director with personal insolvency history | Past financial management failure; may indicate pattern |
| Director with 10+ concurrent directorships | Governance attention necessarily divided; may be a professional nominee |
| Key person dependency (sole director = founder = CEO = spokesperson) | All organisational risk concentrated in one person; no succession, no checks |
| No independent directors on board | No external governance oversight; decisions unchallenged by outsiders |
| Board members all from same network | Echo chamber risk; insufficient diversity of perspective and challenge |

### Operational Red Flags

| Flag | What It Means |
|------|---------------|
| Unverifiable client/partnership claims | Named partners cannot be confirmed through independent sources |
| Impact claims with no metrics | Qualitative claims without quantitative support; may indicate no measurement framework |
| Website vs LinkedIn employee count discrepancy | Inflated team claims or rapid undisclosed turnover |
| Social media purely promotional with no authentic engagement | No genuine community; audience may be purchased or non-existent |
| Job postings open for extended periods | Difficulty attracting talent, high turnover, or non-genuine postings |

---

## 15. Deal-Breaker Signals

Signals of sufficient severity that they should be prominently escalated in any report — not buried in a general risk section. These represent conditions where a reasonable decision-maker would want to know before proceeding.

### Financial Deal-Breakers

- **Going concern signals:** Auditor has expressed doubt about the company's ability to continue operating. This is the most serious financial signal available from public sources.
- **Revenue cliff:** A single contract or client represents more than 30% of revenue and is approaching renewal, expiry, or known risk. Loss of this contract would fundamentally alter the company's financial position.
- **Undisclosed liabilities:** Secured debts visible on PPSR, court judgments, or other obligations not apparent from the company's own disclosures. The gap between disclosed and discoverable liabilities is itself a signal.
- **Tax compliance gaps:** GST registration cancelled, ABN not active, or the ATO appearing as a secured creditor on the PPSR. Tax compliance issues indicate either financial distress or governance failure — both material.

### People Deal-Breakers

- **Founder about to leave:** Reduced public activity, delegation of spokesperson role, new external senior hires in roles previously held by the founder, LinkedIn profile updates suggesting transition. In founder-dependent companies, this changes everything.
- **Mass senior departures within 6-12 months:** Three or more C-suite or senior leadership departures in a short period. Indicates fundamental internal fracture.
- **Shadow directors / undisclosed controllers:** Evidence that someone not listed as a director is actually directing company affairs. This is both a legal issue (shadow director liability) and a governance issue.
- **Disqualified directors:** An individual currently disqualified from managing corporations who is serving as a director. This is a legal violation.
- **Litigation by former insiders:** Former directors, employees, or partners suing the company. Insiders litigate when internal resolution has failed and the issues are severe enough to justify the cost and relationship destruction of litigation.

### Market Deal-Breakers

- **Regulatory discontinuity:** Pending legislation or regulatory change that would fundamentally alter the company's operating model, revenue base, or compliance obligations. Examples: changes to NDIS pricing, new licensing requirements, sector-specific regulatory reform.
- **Market obsolescence:** The company's core product, service, or approach is being superseded by technology, regulatory change, or market evolution, and there is no visible adaptation strategy.
- **Dominant competitor with structural advantages:** A competitor with significantly greater resources, market share, or structural advantages (e.g., exclusive government contracts, proprietary technology, network effects) that makes the subject company's competitive position fundamentally precarious.

### Governance Deal-Breakers

- **Related-party transactions without disclosure:** Money flowing between entities controlled by the same people without transparent disclosure. This is both a legal risk (director duties) and a trust signal.
- **Conflicts of interest:** Directors with interests in competing businesses, suppliers, or customers without disclosure and management.
- **No independent governance:** All board members are insiders, family members, or people with financial interests aligned with management rather than stakeholders.
- **Whistleblower complaints:** Especially to ASIC, IGIS, or other regulators. Formal whistleblower complaints indicate that internal channels have failed and the issues are serious enough for someone to take the significant personal risk of formal reporting.

### Reputation Deal-Breakers

- **Sustained negative media pattern:** Not a single negative article (which can happen to anyone) but a sustained pattern across multiple outlets and time periods, indicating a systemic issue rather than an isolated incident.
- **Customer litigation pattern:** Multiple customers or clients suing for the same or similar issues. This indicates a systemic product, service, or contractual problem rather than an individual dispute.
- **Regulatory enforcement escalation:** A progression from informal warnings to formal notices to prosecution. This pattern indicates that the company has failed to respond to earlier regulatory engagement, and the regulator has escalated.

---

## 16. International Entity Extensions

When a company has international operations, partnerships, or corporate structures extending beyond Australia, equivalent research sources in key jurisdictions.

### United Kingdom
- **Companies House** (find-and-update.company-information.service.gov.uk): Free, comprehensive corporate registry. Includes filing history, directors, persons with significant control (PSC — the UK's beneficial ownership register), annual accounts.
- **Charity Commission** (register-of-charities.charitycommission.gov.uk): If the entity has a UK charity arm. Annual reports, accounts, regulatory actions.
- **The Gazette** (thegazette.co.uk): Official public record. Insolvency notices, winding-up petitions, striking-off notices, statutory notices.

### United States
- **SEC EDGAR** (sec.gov/edgar): For publicly listed companies or those that have issued securities. 10-K (annual reports), 10-Q (quarterly), 8-K (current events), proxy statements.
- **State Secretary of State:** Each US state maintains its own corporate registry. Search the state of incorporation and the state(s) of operation. Delaware, Nevada, and Wyoming are common incorporation states.
- **PACER** (pacer.uscourts.gov): Federal court records. Covers bankruptcy filings, federal litigation. Paid service but invaluable for US litigation history.
- **GuideStar/Candid** (candid.org): For US nonprofits. Form 990 filings, which disclose revenue, expenses, executive compensation, program descriptions, and governance.
- **SAM.gov:** System for Award Management. US government contract awards, entity registration, exclusions (debarment).

### New Zealand
- **Companies Office** (companies.govt.nz): Free, comprehensive. Company details, directors, annual returns, historical filings.
- **Charities Register** (register.charities.govt.nz): NZ registered charities. Annual returns, financial information.

### Singapore
- **ACRA BizFile** (bizfile.gov.sg): Singapore's corporate registry. Company profiles, directors, shareholders, annual filings. Paid searches.

### Global Aggregator
- **OpenCorporates** (opencorporates.com): Aggregates corporate registry data from 140+ jurisdictions. Free for basic searches. Useful for initial identification of entities across multiple countries before conducting detailed searches in individual registries.

---

## 17. Sanctions and Watchlist Screening

**What it is:**
Screening the company, its directors, and its beneficial owners against international sanctions lists, debarment registers, and politically exposed persons (PEP) databases.

**Why it matters:**
Sanctions violations carry severe legal penalties including criminal prosecution. Engaging with a sanctioned entity — even unknowingly — can result in significant legal, financial, and reputational consequences. PEP screening identifies individuals who hold or have held prominent public positions, which elevates corruption and conflict-of-interest risk. This screening is a standard component of formal due diligence and anti-money laundering compliance.

**How to execute it:**

### Australian Sanctions
- **DFAT Consolidated List** (dfat.gov.au/international-relations/security/sanctions/consolidated-list): Australia's consolidated list of all persons and entities subject to targeted financial sanctions and travel bans under Australian sanctions law.
- Search by entity name, individual name, and known aliases.

### United Nations
- **UN Security Council Consolidated List** (scsanctions.un.org): Individuals and entities subject to UN Security Council sanctions. All UN member states are obligated to implement these sanctions.

### United States
- **OFAC SDN List** (sanctionssearch.ofac.treas.gov): The US Office of Foreign Assets Control's Specially Designated Nationals list. Even non-US entities can be affected if they transact in USD or have US nexus.

### European Union
- **EU Consolidated Financial Sanctions List** (data.europa.eu/data/datasets/consolidated-list-of-persons-groups-and-entities-subject-to-eu-financial-sanctions): All persons and entities subject to EU restrictive measures.

### Multilateral Development Banks
- **World Bank Debarment List** (worldbank.org/en/projects-operations/procurement/debarred-firms): Firms and individuals debarred from World Bank-funded projects due to fraud, corruption, collusion, coercion, or obstruction.
- Other multilateral development bank debarment lists (ADB, AfDB, EBRD, IDB) cross-reference through the Agreement for Mutual Enforcement of Debarment Decisions.

### Politically Exposed Persons (PEP) Screening
- PEP screening identifies individuals who are or have been entrusted with a prominent public function: heads of state, senior politicians, senior government officials, judicial or military officials, senior executives of state-owned enterprises, and their family members and close associates.
- PEP status does not imply wrongdoing. It elevates the risk profile because of the potential for corruption, bribery, and conflicts of interest associated with the position.
- PEP databases are typically commercial products (World-Check, Dow Jones Risk & Compliance, LexisNexis WorldCompliance). Flag when PEP screening would be advisable and note that comprehensive PEP screening requires access to commercial databases.

---

## 18. Claim Verification

### Claim Verification

**What it is:** A structured process for verifying a specific factual claim against all available sources before it enters the synthesis. Applies the confidence rating system and flags contradictions.

**When to use:** For any claim that will appear in the Executive Summary, RAG Dashboard, or KIT Answer Register. Do not include a claim in these outputs without running this check.

**Steps:**
1. State the claim precisely (one sentence)
2. Identify the source where this claim originated
3. Search for at least one independent corroborating source
4. Check for contradicting sources
5. Assign confidence: ★★★ (official/audited), ★★ (credible independent), ★ (self-reported/unverified)
6. If contradicted: apply ACH (see `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §8) and flag with ⚠

**Output format:**
```
Claim: [precise statement]
Origin: [source name, type, date]
Corroboration: [source name, type] OR "None found — saturation reached after [N] searches"
Contradiction: [source name, type, nature of contradiction] OR "None"
Confidence: [★★★/★★/★] OR [⚠ contradicted]
```
