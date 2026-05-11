# Australian Data Sources for Company Research

A comprehensive reference of Australian public registers, databases, and intelligence sources for company and organisational research. This document supports the company-intel skill and consolidates the original 8 data sources with all expert-recommended additions.

Last updated: 2026-03-03

---

## 1. Corporate Registration & Identity

### ASIC (Australian Securities & Investments Commission)
- **URL:** https://asic.gov.au
- **What it provides:** Company registration details, ACN, entity type, registered address, date of registration, current status, directors and officeholders (current and historical), shareholders, annual returns, document history.
- **Access:** Free searches via ASIC Connect. Full company extracts and historical documents available for a fee via ASIC Document Ordering.
- **Tips:** Always check the "Current & Historical" details. Director history is invaluable for mapping related entities — search each director's name to find every company they have been or are currently involved with. Track name changes, address shifts, and director rotations over time (the "Shedding Skin" technique). Pay attention to the date of each change — rapid director turnover or frequent name changes can be red flags.

### ABN Lookup (Australian Business Register)
- **URL:** https://abr.business.gov.au
- **What it provides:** ABN, entity name (current and former), entity type, GST registration status and date, main business activity (ANZSIC code), location (state), active/cancelled status.
- **Access:** Free. No registration required.
- **Tips:** Click the "Historical details" tab — this reveals former entity names, previous business names, and changes to GST registration over time. A cancelled ABN followed by a new ABN for a similar entity at the same address is worth investigating. The ANZSIC code reveals how the ATO classifies the business, which may differ from how the company describes itself. Use the ABN Lookup web services API for bulk queries.

### ACNC (Australian Charities and Not-for-profits Commission) Charity Register
- **URL:** https://www.acnc.gov.au/charity
- **What it provides:** Charity details, responsible persons (directors/trustees), Annual Information Statements, financial reports (revenue, expenses, assets, liabilities), size category (small/medium/large), activities and beneficiaries, governing document type, subtype (PBI, DGR, HPC, etc.).
- **Access:** Free. No registration required. Bulk data downloads available.
- **Tips:** Download the bulk data CSV files for benchmarking — these contain financial summaries for all registered charities, enabling sector comparison. The Annual Information Statement often contains richer operational detail than the financial reports alone. Check the "responsible persons" list against ASIC records for cross-entity mapping. The "revoked" and "voluntarily withdrawn" charities are also searchable and can reveal failed entities. Compare self-reported revenue to actual financial statements where both are available.

**Direct API endpoints:**
```bash
# ABR — look up by ABN
curl "https://abr.business.gov.au/json/AbnDetails.aspx?abn={ABN}&callback=callback&guid={GUID}"

# ABR — search by name
curl "https://abr.business.gov.au/json/MatchingNames.aspx?name={encoded_name}&callback=callback&guid={GUID}"

# ASIC — company search (no official public API; use WebSearch or Layer 4)
# ACNC — charity register API
curl "https://www.acnc.gov.au/api/entity/search?q={name}&type=charity"

# OpenCorporates — cross-jurisdiction
curl "https://api.opencorporates.com/v0.4/companies/search?q={name}&jurisdiction_code=au"
```
Note: ABR API requires a GUID (free registration at abr.business.gov.au/Register). If no GUID is available, use WebFetch on the ABR search page instead.

---

## 2. Financial & Credit

### PPSR (Personal Property Securities Register)
- **URL:** https://www.ppsr.gov.au
- **What it provides:** Secured interests in personal property (not real property). Reveals who has security interests over a company's assets — typically banks, equipment financiers, and trade creditors. Shows ALLPAAP (All Present and After-Acquired Property) charges, specific asset registrations, and serial-numbered goods.
- **Access:** Free searches by organisation name or ACN. $2 per grantor search for full results.
- **Tips:** An ALLPAAP registration usually indicates a bank facility — the bank name reveals the primary banking relationship. Multiple finance company registrations may indicate asset-heavy operations or reliance on equipment finance. A sudden increase in PPSR registrations can signal financial distress. The absence of any PPSR registrations for a company that claims substantial assets is itself notable. Use PPSR data to verify claims about asset ownership.

### ASIC Document Ordering
- **URL:** https://asic.gov.au/online-services/search-asics-registers/
- **What it provides:** Full company extracts (current and historical), annual returns, financial reports, constitution documents, change of name certificates, change of officeholder notifications, and all historical filings.
- **Access:** Paid. Prices range from $9 for a current extract to $42+ for historical company extract. Payment via credit card.
- **Tips:** Historical company extracts are the gold standard for tracking a company's evolution. Annual returns (for proprietary companies) reveal shareholder changes over time. Request the "Document List" first ($9) to see what is available before ordering expensive documents. Financial reports are only lodged by large proprietary companies and public companies — most Pty Ltds do not file financials with ASIC.

### AFSA (Australian Financial Security Authority)
- **URL:** https://www.afsa.gov.au/online-services/bankruptcy-register-search
- **What it provides:** National Personal Insolvency Index (NPII) — records of personal bankruptcies, debt agreements, and personal insolvency agreements for individuals.
- **Access:** Free search. Provides name, state, and administration type. Full details available for a fee.
- **Tips:** Search key directors and officeholders. A director with a personal insolvency history may be disqualified from managing corporations under the Corporations Act. Cross-reference with the ASIC Banned & Disqualified Register. Also useful for tracing individuals who have been involved in failed businesses.

### ASIC Published Notices
- **URL:** https://insolvencynotices.asic.gov.au
- **What it provides:** Notices of external administration — voluntary administration, liquidation, receivership, controller appointments. Also includes notices of deregistration and striking off.
- **Access:** Free. Searchable by company name or practitioner.
- **Tips:** Search not just the target company but also every related entity (same directors, same address). A pattern of entities entering insolvency around the same people is a significant red flag. The practitioner name can also be searched to find all their current matters. Check for "phoenix" patterns — new entity registered shortly after a related entity enters liquidation.

### Commercial Credit Services
- **CreditorWatch:** https://www.creditorwatch.com.au — Credit reports, payment defaults, court actions, ASIC notices, cross-directorships, risk scoring.
- **illion (formerly Dun & Bradstreet Australia):** https://www.illion.com.au — Credit reports, DUNS number, payment behaviour, financial risk assessment.
- **Equifax (formerly Veda):** https://www.equifax.com.au/business — Commercial credit reports, director reports, risk scores.
- **Access:** All paid services. Subscriptions or per-report pricing. CreditorWatch offers some data via a free trial.
- **Tips:** These services aggregate data from ASIC, PPSR, courts, and trade creditors into a single report. Useful when you need a consolidated view quickly. The real value is in payment default data and trade credit behaviour, which is not available from any free source. Director reports from these services map all company involvements for an individual in one place.

**Paywalled source protocol:**
When a paywalled source is the most authoritative source for a KIT answer:
1. Note it as inaccessible in `inaccessible-sources.md` with failure mode: `Paywalled — no free access`
2. Search for a free proxy: academic open access, author's ResearchGate page, press release summarising findings, or trade press coverage
3. If a free proxy exists, use it with ★★ rating (not ★★★ — the proxy may summarise selectively)
4. If no free proxy exists, note the gap explicitly in the Information Gaps Register and state what the paywalled source would have answered

---

## 3. Government Procurement

### AusTender (Federal)
- **URL:** https://www.tenders.gov.au
- **What it provides:** Federal government procurement — open tenders, contract notices (awarded contracts including value, supplier, category, agency), standing offers, and multi-use lists. Historical contract data going back many years.
- **Access:** Free. No registration required for searching. Registration required to respond to tenders.
- **Tips:** Search by supplier name to find all federal contracts a company has won. Contract notices include the value, start/end dates, category, and the government agency. This reveals government revenue, client relationships, and contract expiry dates (useful for timing intelligence). The "CN" (Contract Notice) data is the most valuable — it shows actual awarded contracts, not just opportunities. Export results to CSV for analysis.

### GrantConnect
- **URL:** https://www.grants.gov.au
- **What it provides:** Federal government grants — grant opportunities (open, closed, upcoming) and grant outcomes (who received funding, how much, for what purpose).
- **Access:** Free. Registration required for some features.
- **Tips:** The "Grants Awarded" or outcomes data is the intelligence goldmine. Search by recipient to find all federal grants a company or organisation has received. Reveals funding dependency and government relationships. Grant program guidelines also show the strategic priorities of government agencies, which helps predict future opportunities.

### State & Territory Tender Portals

#### VicTenders / Buying for Victoria
- **URL:** https://www.buyingfor.vic.gov.au
- **What it provides:** Victorian Government procurement opportunities, awarded contracts, supplier panels.
- **Access:** Free.
- **Tips:** Victoria's social procurement framework (SPF) is mandatory for all government procurement. Check awarded contracts for social enterprise suppliers. The "Contracts Publishing System" shows awarded contracts including value and supplier details.

#### NSW eTendering
- **URL:** https://www.tenders.nsw.gov.au
- **What it provides:** NSW Government tenders and awarded contracts.
- **Access:** Free. Registration required for full functionality.

#### QTenders (Queensland)
- **URL:** https://www.forgov.qld.gov.au/qtenders
- **What it provides:** Queensland Government procurement opportunities and awarded contracts.
- **Access:** Free.

#### SA Tenders (South Australia)
- **URL:** https://www.tenders.sa.gov.au
- **What it provides:** South Australian Government tenders and contracts.
- **Access:** Free.

#### WA Tenders (Western Australia)
- **URL:** https://www.tenders.wa.gov.au
- **What it provides:** Western Australian Government tenders and contracts.
- **Access:** Free.

### DTA Digital Marketplace
- **URL:** https://marketplace.service.gov.au
- **What it provides:** Australian Government's marketplace for digital and ICT procurement. Seller profiles, awarded contracts, and procurement opportunities.
- **Access:** Free. Registration as a buyer or seller required for participation.
- **Tips:** The seller profiles reveal capabilities, case studies, and contract history for digital/ICT companies. A useful source for understanding a company's technology services and government digital work.

---

## 4. Courts & Tribunals

### AustLII (Australasian Legal Information Institute)
- **URL:** https://www.austlii.edu.au
- **What it provides:** The primary free legal database for Australia. Case law from all Australian courts and tribunals — High Court, Federal Court, Federal Circuit Court, all state/territory Supreme Courts, many lower courts, and key tribunals. Also legislation, journals, and treaties.
- **Access:** Free. No registration required.
- **Tips:** Search by company name, ABN/ACN, director names, and trading names. Use the "Databases" page to search specific jurisdictions. Not all decisions are published — lower court and tribunal decisions are less consistently available. AustLII is the single best starting point for legal research, but should be supplemented with court-specific searches for comprehensive coverage. Use the advanced search to filter by jurisdiction and date range.

### Federal Court of Australia
- **URL:** https://www.fedcourt.gov.au
- **What it provides:** Federal Court judgments, case lists, daily court lists. Covers corporate insolvency, intellectual property, competition law, migration, native title, and admiralty matters.
- **Access:** Free. Judgments available on the website and via AustLII.
- **Tips:** The Federal Court's search function on its own website can sometimes return results not yet on AustLII. Check the daily court lists for upcoming matters involving your target.

### High Court of Australia
- **URL:** https://www.hcourt.gov.au
- **What it provides:** High Court judgments, transcripts of proceedings, case summaries, and special leave applications.
- **Access:** Free.
- **Tips:** Only the most significant cases reach the High Court. If a company is involved in High Court proceedings, it indicates a matter of substantial legal significance.

### AAT/ART (Administrative Appeals Tribunal / Administrative Review Tribunal)
- **URL:** https://www.aat.gov.au (transitioning to ART)
- **What it provides:** Decisions on review of government administrative decisions — taxation, migration, social services, veterans' affairs, NDIS, and other Commonwealth decisions.
- **Access:** Free. Decisions searchable via AustLII and the tribunal's own website.
- **Tips:** AAT tax decisions can reveal disputes between a company and the ATO. Search by company name and director names. The AAT has been transitioning to the Administrative Review Tribunal (ART) — check both.

### Fair Work Commission
- **URL:** https://www.fwc.gov.au
- **What it provides:** Decisions on unfair dismissal claims, enterprise bargaining disputes, industrial action, general protections, and workplace disputes.
- **Access:** Free. Decisions available on the FWC website and AustLII.
- **Tips:** Unfair dismissal claims against a company can reveal management practices, workplace culture issues, and internal disputes. Enterprise agreements reveal pay structures and working conditions. Search by employer name.

### State Courts

#### Supreme Courts (all states/territories)
- Hear the most serious civil and criminal matters. Commercial disputes, insolvency proceedings, significant contract disputes. Judgments available via AustLII and individual court websites.

#### County/District Courts
- Mid-tier civil matters (typically $100K–$750K depending on jurisdiction). Less consistently published online. Check AustLII and individual court websites.

#### Magistrates' Courts
- Lower-value civil disputes, minor criminal matters, intervention orders. Decisions rarely published online. May need to search court records in person or via formal request.

### State Tribunals

#### VCAT (Victorian Civil and Administrative Tribunal)
- **URL:** https://www.vcat.vic.gov.au
- **What it provides:** Decisions on planning, building, owners corporations, tenancy, civil claims, human rights, guardianship, and other administrative review in Victoria.
- **Access:** Free. Decisions via AustLII.

#### NCAT (NSW Civil and Administrative Tribunal)
- **URL:** https://www.ncat.nsw.gov.au
- **What it provides:** Consumer claims, administrative review, tenancy, guardianship, and occupational licensing decisions in NSW.
- **Access:** Free. Decisions via AustLII.

#### QCAT (Queensland Civil and Administrative Tribunal)
- **URL:** https://www.qcat.qld.gov.au
- **What it provides:** Consumer disputes, administrative review, minor civil disputes, guardianship, and anti-discrimination matters in Queensland.
- **Access:** Free. Decisions via AustLII.

### ACCC (Australian Competition & Consumer Commission)
- **URL:** https://www.accc.gov.au
- **What it provides:** Enforcement actions, court proceedings, enforceable undertakings, infringement notices, merger authorisations, and compliance guidance. The "Enforcement" and "Public registers" sections are the most relevant.
- **Access:** Free.
- **Tips:** The ACCC's "Enforceable Undertakings" register is particularly valuable — these are legally binding commitments by companies to change conduct, often in response to competition or consumer law breaches. The "Courts and Enforcement" section lists all ACCC enforcement actions. Also check the "Scamwatch" and "Product Safety" sections. ACCC media releases announce new enforcement actions and outcomes.

---

## 5. Regulatory & Professional Registers

### ASIC Banned & Disqualified Register
- **URL:** https://asic.gov.au/online-services/search-asics-registers/banned-and-disqualified/
- **What it provides:** Individuals banned or disqualified from providing financial services, managing corporations, or acting as auditors.
- **Access:** Free.
- **Tips:** Search every director and key person. A ban or disqualification is a critical red flag. Check historical names as well — some individuals change their name after a banning order.

### AFSL Register (Australian Financial Services Licence)
- **URL:** https://www.moneysmart.gov.au/investing/financial-advice/financial-advisers-register
- **What it provides:** Details of all AFSL holders and authorised representatives — licence conditions, authorisations, what financial services they can provide, and who their authorised representatives are.
- **Access:** Free.
- **Tips:** If a company provides financial services, check that they hold the appropriate licence. The licence conditions reveal exactly what they are authorised to do. Also check if any conditions have been varied or if enforcement action has been taken.

### ACL Register (Australian Credit Licence)
- **URL:** https://www.moneysmart.gov.au/borrowing-and-credit/credit-licences
- **What it provides:** Details of Australian Credit Licence holders — who can provide credit services, broker mortgages, or engage in credit activities.
- **Access:** Free.

### AHPRA (Australian Health Practitioner Regulation Agency)
- **URL:** https://www.ahpra.gov.au
- **What it provides:** Registration details of health practitioners (doctors, nurses, dentists, psychologists, pharmacists, etc.) — current registration status, any conditions or undertakings, disciplinary history.
- **Access:** Free via the public register search.
- **Tips:** Essential for any company in health services. Check the registration status of all clinical staff mentioned on the website. Conditions or undertakings on registration are significant findings.

### NDIS Quality & Safeguards Commission
- **URL:** https://www.ndiscommission.gov.au
- **What it provides:** Registered NDIS provider search, compliance and enforcement actions, banning orders, conditions on registration.
- **Access:** Free. Provider register is searchable.
- **Tips:** For any company providing NDIS services, verify their registration status and check for any compliance actions. The Commission publishes enforcement outcomes including banning orders and conditions.

### Aged Care Quality & Safety Commission
- **URL:** https://www.agedcarequality.gov.au
- **What it provides:** Approved provider register, compliance ratings, accreditation status, sanction history, star ratings for residential aged care.
- **Access:** Free.
- **Tips:** Check "Find a Provider" for current accreditation status and any sanctions. The star rating system provides a quick quality indicator. Non-compliance notices are published.

### EPA Registers (State-level)
- **EPA Victoria:** https://www.epa.vic.gov.au
- **EPA NSW:** https://www.epa.nsw.gov.au
- **EPA Queensland (DES):** https://www.des.qld.gov.au
- **EPA South Australia:** https://www.epa.sa.gov.au
- **DWER Western Australia:** https://www.dwer.wa.gov.au
- **What they provide:** Environment protection licences, pollution incident notifications, compliance and enforcement actions, contaminated site registers, licence conditions.
- **Access:** Free. Most have searchable online registers.
- **Tips:** Environmental licences and enforcement actions reveal operational risks. Contaminated site registers are critical for property-related due diligence.

### SafeWork / WorkSafe (State-level)
- **SafeWork NSW:** https://www.safework.nsw.gov.au
- **WorkSafe Victoria:** https://www.worksafe.vic.gov.au
- **Workplace Health and Safety QLD:** https://www.worksafe.qld.gov.au
- **SafeWork SA:** https://www.safework.sa.gov.au
- **WorkSafe WA:** https://www.commerce.wa.gov.au/worksafe
- **What they provide:** Workplace safety enforcement actions, prosecution outcomes, prohibition and improvement notices, incident reports.
- **Access:** Varies by state. Prosecution outcomes generally published. Some registers require formal requests.
- **Tips:** Search for the company name in prosecution databases. Workplace safety prosecutions indicate operational risk and management culture. Enforceable undertakings (WHS) are also published by most regulators.

### Modern Slavery Register
- **URL:** https://modernslaveryregister.gov.au
- **What it provides:** Modern slavery statements lodged by entities with consolidated revenue of $100M+ (mandatory) and voluntary reporters. Statements describe the entity's operations, supply chains, risks of modern slavery, and actions taken.
- **Access:** Free. All statements are publicly downloadable.
- **Tips:** Large companies and their subsidiaries are required to report. The statements reveal supply chain structures, overseas operations, and risk management maturity. Voluntary reporters may be signalling values-based leadership. The absence of a statement from a company that should be reporting is a red flag.

### OAIC (Office of the Australian Information Commissioner) — Notifiable Data Breaches
- **URL:** https://www.oaic.gov.au/privacy/notifiable-data-breaches
- **What it provides:** Statistics and reports on notifiable data breaches. Specific breach notifications are not individually published by company name, but the OAIC publishes enforcement actions, determinations, and investigations that name organisations.
- **Access:** Free.
- **Tips:** Search for the company in OAIC enforcement actions and determinations. The biannual Notifiable Data Breaches report provides sector-level statistics. Media reports often name companies involved in significant breaches.

### ACMA (Australian Communications and Media Authority)
- **URL:** https://www.acma.gov.au
- **What it provides:** Enforcement actions for breaches of telecommunications, broadcasting, spam, and Do Not Call Register legislation. Licence registers for broadcasting and radiocommunications.
- **Access:** Free.
- **Tips:** Check the "Compliance and enforcement" section for any actions against the target company. The investigations register is searchable. Relevant for media, telecommunications, and any company engaging in telemarketing or commercial electronic messaging.

### CASA (Civil Aviation Safety Authority)
- **URL:** https://www.casa.gov.au
- **What it provides:** Aviation operator certificates, pilot licences, aircraft register, enforcement actions, safety reports.
- **Access:** Free for public register searches.
- **Tips:** Relevant for aviation companies, drone operators, and air transport businesses. The operator register confirms whether a company holds valid aviation certificates.

### ORIC (Office of the Registrar of Indigenous Corporations)
- **URL:** https://www.oric.gov.au
- **What it provides:** Register of Aboriginal and Torres Strait Islander corporations — incorporation details, rule books, reports, compliance history, special administrations.
- **Access:** Free. Register is searchable.
- **Tips:** Essential for any company structured as an Indigenous corporation under the CATSI Act. ORIC publishes annual reports of corporations, special administration notices, and compliance actions.

### APRA (Australian Prudential Regulation Authority)
- **URL:** https://www.apra.gov.au
- **What it provides:** Register of APRA-regulated entities (banks, insurers, superannuation funds), prudential statistics, enforcement actions, licence conditions.
- **Access:** Free. Statistics and enforcement actions published.
- **Tips:** APRA publishes detailed prudential statistics for regulated entities. Enforcement actions are published as media releases and on the enforcement register. Essential for any company in banking, insurance, or superannuation.

### TGA (Therapeutic Goods Administration)
- **URL:** https://www.tga.gov.au
- **What it provides:** Australian Register of Therapeutic Goods (ARTG) — registered medicines, medical devices, biologicals. Recalls, safety alerts, compliance actions, advertising complaints outcomes.
- **Access:** Free. ARTG is searchable.
- **Tips:** For any company in pharmaceuticals, medical devices, or complementary medicines, verify their products are properly registered. Check for recalls, safety alerts, and compliance actions. The advertising complaints register reveals marketing compliance issues.

### State Law Societies
- **Law Society of NSW:** https://www.lawsociety.com.au
- **Law Society of Victoria (LIV):** https://www.liv.asn.au
- **Queensland Law Society:** https://www.qls.com.au
- **Law Society of SA:** https://www.lawsociety.asn.au
- **Law Society of WA:** https://www.lawsociety.asn.au
- **What they provide:** Solicitor registers (practising certificate status), disciplinary actions, trust account issues.
- **Access:** Free for basic register searches. Some details behind membership access.
- **Tips:** For law firms or companies with in-house legal teams, verify practising certificates. Disciplinary actions are published by the relevant Legal Services Commissioner in each state.

### CPA / CA Registers
- **CPA Australia:** https://www.cpaaustralia.com.au — Find a CPA search
- **Chartered Accountants ANZ (CA ANZ):** https://www.charteredaccountantsanz.com — Find a CA search
- **What they provide:** Membership verification, practising certificate status, disciplinary actions.
- **Access:** Free register searches.
- **Tips:** For accounting firms or companies claiming CPA/CA credentials, verify membership status. Disciplinary actions are published.

### Engineers Australia
- **URL:** https://www.engineersaustralia.org.au
- **What it provides:** National Engineering Register (NER), chartered engineer status, disciplinary actions.
- **Access:** Free register search.
- **Tips:** For engineering companies, verify chartered status of key staff. Cross-reference claims of engineering qualifications.

### RTO Register (training.gov.au)
- **URL:** https://training.gov.au
- **What it provides:** Registered Training Organisations — registration status, scope of registration (what qualifications they can deliver), compliance history, ASQA audit outcomes.
- **Access:** Free.
- **Tips:** For any company delivering nationally recognised training. Verify registration is current and the specific qualifications are within their scope. ASQA (Australian Skills Quality Authority) publishes compliance actions against RTOs including sanctions and cancellations.

---

## 6. Social Enterprise & NFP

### Social Traders Directory
- **URL:** https://www.socialtraders.com.au/find-a-social-enterprise/
- **What it provides:** Directory of certified social enterprises in Australia. Includes certification tier (Provisional, Certified, Advanced), service categories, procurement categories, location, beneficiary groups, and social impact summary.
- **Access:** Free to browse. Social Traders charges for certification (paid by the social enterprise, not the searcher).
- **Tips:** Social Traders is the primary certification body for social enterprises in Australia. Certification tiers indicate maturity — Advanced certification requires demonstrated impact measurement and financial sustainability. The procurement categories align with government social procurement frameworks, particularly Victoria's SPF. Use the directory to identify competitors, benchmarks, and potential partners in the social enterprise space. If a company claims social enterprise status but is not in this directory, ask why.

### Supply Nation
- **URL:** https://www.supplynation.org.au
- **What it provides:** Directory of verified Indigenous businesses. Supply Nation certification confirms at least 50% Indigenous ownership. Includes business profiles, capability statements, industry categories, and location.
- **Access:** Free to search the directory. Full features require membership.
- **Tips:** Supply Nation certification is the gold standard for verifying Indigenous business status. Required for most government and corporate Indigenous procurement programs. Check the certification level — "Registered" vs "Certified" vs "Certified Supplier" have different verification levels. Also lists Indigenous businesses that are "Supply Nation members" but not yet certified.

### B Corp Directory
- **URL:** https://www.bcorporation.net/en-us/find-a-b-corp/
- **What it provides:** Global directory of Certified B Corporations — verified via the B Impact Assessment across governance, workers, community, environment, and customers. Includes the company's B Impact Score (out of 200, minimum 80 to certify), industry, size, and score breakdown by impact area.
- **Access:** Free.
- **Tips:** The B Impact Score and its breakdown reveal where a company is strongest and weakest on social/environmental performance. Compare scores against industry peers. Recertification is required every three years — check the certification date to ensure it is current. Some companies let certification lapse, which is worth investigating.

### Pro Bono Australia
- **URL:** https://probonoaustralia.com.au
- **What it provides:** News, jobs, and resources for the Australian NFP sector. Job board reveals organisational structure and hiring patterns. News section covers sector developments, policy changes, and organisational stories.
- **Access:** Free. Some content behind membership.
- **Tips:** Search for the target organisation in news articles for sector-specific coverage not found in mainstream media. The job board reveals salary ranges (often listed), organisational culture, and strategic direction. Sector-specific news is often more detailed than mainstream coverage.

### Our Community / GiveNow
- **URL:** https://www.ourcommunity.com.au / https://www.givenow.com.au
- **What it provides:** Our Community provides resources, training, and tools for NFPs. GiveNow is a donation platform — listed charities include profiles with descriptions and financial information. GiveNow listings reveal fundraising activity and public positioning.
- **Access:** Free.
- **Tips:** GiveNow profiles show how an organisation presents itself to potential donors, which may differ from how it presents to government or commercial partners. Our Community's grants hub (GrantFinder) reveals what grants organisations are seeking.

### Infoxchange Service Seeker
- **URL:** https://www.serviceseeker.com.au
- **What it provides:** Directory of community and health services across Australia. Reveals service types, locations, target groups, and service delivery areas.
- **Access:** Free.
- **Tips:** Useful for mapping the service delivery footprint of community organisations and health services. Reveals what services a target organisation actually delivers on the ground, as opposed to what they claim on their website.

### State Social Enterprise Networks
- **SENVIC (Social Enterprise Network Victoria):** https://www.senvic.org.au
- **SENSW (Social Enterprise Network NSW):** Active via social media and events
- **QSEC (Queensland Social Enterprise Council):** https://www.qsec.org.au
- **SESA (Social Enterprise South Australia):** Community-based network
- **What they provide:** Directories of local social enterprises, events, networking, and advocacy. Member directories reveal the social enterprise ecosystem in each state.
- **Access:** Free to browse. Membership-based networks.
- **Tips:** These networks often have more granular local knowledge than the national directories. Membership in a state network indicates engagement with the local social enterprise community. Events and publications reveal sector trends and emerging organisations.

### Impact Investing Australia
- **URL:** https://impactinvestingaustralia.com
- **What it provides:** Information on impact investment deals, funds, and intermediaries in Australia. Publishes benchmark reports, deal data, and investor profiles.
- **Access:** Free for public resources. Some content is member-only.
- **Tips:** Useful for understanding the impact investment landscape and identifying whether a target organisation has received impact investment. The annual benchmark report provides market data.

### Philanthropy Australia
- **URL:** https://www.philanthropy.org.au
- **What it provides:** Membership directory of philanthropic foundations and trusts. Resources on giving trends, grant-making, and philanthropic strategy.
- **Access:** Free for some resources. Member directory may require membership.
- **Tips:** Identify potential funders or existing funding relationships. The member directory reveals which foundations are active in specific sectors.

### Kinaway (Victorian Aboriginal Chamber of Commerce)
- **URL:** https://kinaway.com.au
- **What it provides:** Directory of Victorian Aboriginal businesses. Verification of Aboriginal business status. Business profiles and capability information.
- **Access:** Free to search.
- **Tips:** For Victorian-based research, Kinaway complements Supply Nation with a more granular local directory. Kinaway membership indicates engagement with the Victorian Aboriginal business community.

### Social Procurement Australia
- **URL:** https://www.socialprocurementaustralia.com
- **What it provides:** Resources and advocacy for social procurement. Connects buyers with social enterprises. Social procurement readiness assessments.
- **Access:** Free for some resources.
- **Tips:** Useful for understanding procurement opportunities available to social enterprises and which buyers are actively engaged in social procurement.

---

## 7. Property & Land

### Landata (Victoria)
- **URL:** https://www.landata.vic.gov.au
- **What it provides:** Victorian land title searches — registered proprietor (owner), lot and plan details, encumbrances, mortgages, caveats, easements, covenants, and historical transfer records.
- **Access:** Paid. Title searches from approximately $7 per search via Landata online. Volume pricing available.
- **Tips:** Reveals who actually owns a property (as opposed to who occupies it). Mortgages show the lender and potentially the borrowing amount. Caveats can indicate disputes or unregistered interests. Historical searches show the chain of ownership and can reveal related-party transfers. Cross-reference with council rate records for additional owner details.

### NSW LRS (NSW Land Registry Services)
- **URL:** https://www.nswlrs.com.au
- **What it provides:** NSW land title searches — same core information as Victoria: proprietor details, mortgages, caveats, easements, and dealings history.
- **Access:** Paid. Searches available via the online portal.
- **Tips:** The "Dealings History" reveals all recorded transactions on the title. NSW LRS also provides historical title searches and plan information.

### QLD Titles Registry
- **URL:** https://www.titlesqld.com.au
- **What it provides:** Queensland land title searches — registered owner, lot on plan, encumbrances, mortgages, and dealings.
- **Access:** Paid. Online searches available.
- **Tips:** Queensland titles also record administrative advices (e.g., contaminated land notifications). Check for any registered interests that might affect the property's value or use.

### SAILIS (South Australia Integrated Land Information System)
- **URL:** https://www.sailis.sa.gov.au
- **What it provides:** South Australian land title searches — proprietor, encumbrances, mortgages, caveats.
- **Access:** Paid. Online access available.

### Landgate (Western Australia)
- **URL:** https://www.landgate.wa.gov.au
- **What it provides:** WA land title searches, property valuation data, survey information, pastoral lease information.
- **Access:** Paid. Online searches available. Some property valuation data available via the Property Interest Report.
- **Tips:** Landgate also provides aerial imagery and property valuation data which can supplement title search information. The Property Interest Report provides a summary of all registered interests.

**General property search tips:** Always search for properties at the registered address of the company and at the residential addresses of directors (where disclosed). Property ownership can reveal hidden wealth, related-party transactions, and asset-backing (or lack thereof). Compare the registered address with actual property ownership — companies operating from premises they do not own may be tenants, which has implications for asset-based assessments.

---

## 8. Planning & Environment

### Council DA Registers (Development Application Registers)
- **URL:** Individual council websites. Most councils have online DA tracking.
- **What it provides:** Development applications lodged, approved, or refused. Includes plans, applicant details, objections, and conditions of approval. Reveals building works, change of use, subdivisions, and demolitions.
- **Access:** Free on most council websites. Some use third-party platforms like Application Tracking or ePlanning.
- **Tips:** Search by address, applicant name, or lot number. DAs reveal planned expansions, new developments, and property use changes. Objections from neighbours can reveal community sentiment. The applicant name may be a trustee or developer entity connected to the target.

### State Planning Portals

#### NSW Planning Portal
- **URL:** https://www.planningportal.nsw.gov.au
- **What it provides:** Centralised access to development applications and planning proposals across NSW. State Significant Development (SSD) and State Significant Infrastructure (SSI) applications.
- **Access:** Free.
- **Tips:** Major developments are tracked here — useful for large-scale projects involving the target company or their properties.

#### VicSmart / Planning Victoria
- **URL:** https://www.planning.vic.gov.au
- **What it provides:** Victorian planning scheme information, amendments, and ministerial decisions. VicSmart is a fast-track assessment pathway for minor applications.
- **Access:** Free.

### NPI (National Pollutant Inventory)
- **URL:** https://www.npi.gov.au
- **What it provides:** Facility-level data on emissions and transfers of 93 substances reported by industrial facilities across Australia. Searchable by facility, substance, location, or industry.
- **Access:** Free.
- **Tips:** If the target company operates industrial facilities, NPI data reveals what pollutants they emit and in what quantities. Year-on-year trends show whether emissions are increasing or decreasing. Useful for environmental due diligence and ESG assessment.

### State EPA Registers
- See Section 5 (Regulatory & Professional Registers) for EPA contact details.
- **What they provide:** In the planning and environment context — contaminated site registers, pollution licences, environmental audit reports, and works approval conditions.
- **Access:** Free for most registers.
- **Tips:** The contaminated site register is essential for property-related due diligence. EPA pollution licences reveal operational conditions and monitoring requirements. Non-compliance with licence conditions is published in enforcement registers.

### NGER (National Greenhouse and Energy Reporting)
- **URL:** https://www.cleanenergyregulator.gov.au/NGER
- **What it provides:** Greenhouse gas emissions, energy production, and energy consumption data reported by corporations meeting reporting thresholds. Published data includes facility-level and corporate-level emissions.
- **Access:** Free. Published data available on the Clean Energy Regulator website.
- **Tips:** Companies that meet the reporting threshold (25 kilotonnes CO2-e at facility level or 50 kilotonnes at corporate level) must report. The published data reveals the carbon footprint of major emitters. Useful for ESG assessment and understanding environmental risk.

### Clean Energy Regulator
- **URL:** https://www.cleanenergyregulator.gov.au
- **What it provides:** In addition to NGER data — Renewable Energy Target (RET) data, carbon credit (ACCU) holdings and transactions, Safeguard Mechanism baselines and compliance, and Emissions Reduction Fund project data.
- **Access:** Free.
- **Tips:** Check whether the target company participates in the ERF, holds ACCUs, or has a Safeguard Mechanism baseline. This data reveals climate-related regulatory exposure and compliance obligations.

---

## 9. Government Accountability

### Parliamentary Hansard
- **URL:** https://parlinfo.aph.gov.au
- **What it provides:** Transcripts of all proceedings in the Australian Parliament — House of Representatives and Senate debates, question time, ministerial statements, and tabling of documents. Also includes committee reports, submissions, and hearing transcripts.
- **Access:** Free. Fully searchable via ParlInfo.
- **Tips:** Search for the company name in Hansard to discover whether it has been mentioned in parliamentary debate — this may reveal political controversy, lobbying activity, or government scrutiny. Committee hearings are particularly rich — Senate Estimates hearings often contain detailed questioning about government contracts, grants, and regulatory decisions. Committee inquiry submissions reveal what positions organisations take on policy issues.

### Senate Estimates & Committee Reports
- **URL:** https://parlinfo.aph.gov.au (committees section) and https://www.aph.gov.au/Parliamentary_Business/Committees
- **What it provides:** Senate Estimates transcripts (questioning of government officials about expenditure and program delivery), committee inquiry reports, submissions, and hearing transcripts.
- **Access:** Free.
- **Tips:** Senate Estimates is where government contracts, grants, and regulatory decisions get scrutinised in detail. Search for the company name in Estimates Hansard to find any discussions about contracts or funding. Committee inquiry submissions by the target company reveal their policy positions and advocacy.

### FOI Disclosure Logs (Federal & State)
- **Federal:** Each Commonwealth agency maintains its own disclosure log. Start at https://www.oaic.gov.au
- **State:** Each state has its own FOI regime and disclosure log requirements.
- **What they provide:** Documents released under Freedom of Information. Disclosure logs contain documents that have been released to applicants and are deemed to be of general public interest.
- **Access:** Free.
- **Tips:** Search disclosure logs of agencies the target company interacts with (the agency that awarded their contract, their regulator, etc.). FOI releases can contain contracts, internal assessments, correspondence, and briefing papers. Not all released documents appear on disclosure logs — you may need to lodge your own FOI request for specific documents.

### Auditor-General Reports

#### ANAO (Australian National Audit Office)
- **URL:** https://www.anao.gov.au
- **What it provides:** Performance audits and financial statement audits of Commonwealth agencies and programs. Reports often name specific contractors, grant recipients, and service providers.
- **Access:** Free. All reports published online.
- **Tips:** Search for the company name in ANAO reports. Performance audits of government programs may assess the effectiveness of contracts the target company holds. These reports can reveal contract performance issues, cost overruns, and compliance concerns.

#### State Auditors-General
- **VAGO (Victoria):** https://www.audit.vic.gov.au
- **Audit Office of NSW:** https://www.audit.nsw.gov.au
- **QAO (Queensland):** https://www.qao.qld.gov.au
- **SAAG (South Australia):** https://www.audit.sa.gov.au
- **OAG WA (Western Australia):** https://audit.wa.gov.au
- **What they provide:** Performance audits and financial audits of state government agencies, programs, and services.
- **Access:** Free.

### Ombudsman Reports
- **Commonwealth Ombudsman:** https://www.ombudsman.gov.au
- **State Ombudsmen:** Each state has its own Ombudsman.
- **What they provide:** Investigation reports into maladministration by government agencies. May name service providers and contractors involved in systemic issues.
- **Access:** Free.
- **Tips:** Ombudsman investigations into government programs may reveal issues with contracted service providers. These reports can contain findings about service quality, compliance, and complaint handling.

### Royal Commission Transcripts
- **URL:** Various — each Royal Commission has its own website. Many archived via the National Library of Australia.
- **What it provides:** Transcripts of evidence, submissions, exhibits, and final reports from Royal Commissions. Companies and individuals giving evidence are named.
- **Access:** Free. Most are archived and searchable.
- **Tips:** Notable Royal Commissions with corporate relevance include: Banking Royal Commission (financial services), Aged Care Quality and Safety, Disability (NDIS), Robodebt, and the Trade Union Royal Commission. Search for the company name and key individuals in transcripts and submissions. Being named in Royal Commission proceedings is highly significant.

---

## 10. Political & Lobbying

### AEC Transparency Register (Political Donations)
- **URL:** https://transparency.aec.gov.au
- **What it provides:** Annual returns from political parties, associated entities, donors, and third-party campaigners. Reveals political donations above the disclosure threshold (currently $16,900 for 2024-25, indexed annually). Includes the donor name, amount, and recipient party.
- **Access:** Free. Searchable and downloadable.
- **Tips:** Search for the company name and the names of key directors. Political donations reveal relationships and potential conflicts of interest. Note that the disclosure threshold means smaller donations are not captured. Returns are published annually with a significant time lag (typically 12+ months). Some donations may be made through associated entities or trusts that are harder to trace.

### Australian Government Register of Lobbyists
- **URL:** https://lobbyists.pmc.gov.au
- **What it provides:** Register of third-party lobbyists (those who lobby government on behalf of clients). Shows the lobbying firm, the lobbyists employed, and (critically) their clients — the entities on whose behalf they lobby.
- **Access:** Free.
- **Tips:** Search for the company name as a client of a lobbyist. This reveals who is lobbying government on their behalf and by implication what policy or procurement outcomes they are seeking. Also search for former politicians or senior public servants now registered as lobbyists — the "revolving door" between government and lobbying is a significant intelligence indicator.

### State Lobbyist Registers
- **Victoria:** https://www.lobbyistsregister.vic.gov.au
- **NSW:** https://lobbyists.nsw.gov.au
- **Queensland:** https://lobbyists.integrity.qld.gov.au
- **South Australia:** https://lobbyists.sa.gov.au
- **Western Australia:** https://www.lobbyists.wa.gov.au
- **What they provide:** Same concept as the federal register — third-party lobbyists and their clients, at the state level.
- **Access:** Free.
- **Tips:** State lobbyist registers capture lobbying of state government. Some states also require in-house lobbyists (company employees who lobby) to register, not just third-party lobbyists. The rules vary by state.

---

## 11. Historical & Archival

### Trove (National Library of Australia)
- **URL:** https://trove.nla.gov.au
- **What it provides:** Digitised newspapers (historical), books, images, maps, music, Government Gazette entries, archived websites, and other library collections. The digitised newspaper archive is the primary intelligence resource — covers Australian newspapers from the 1800s to recent decades.
- **Access:** Free.
- **Tips:** Search for the company name, founder names, and previous company names in the newspaper archive. Historical newspaper coverage can reveal a company's origins, controversies, legal proceedings, and evolution that may no longer be available online. Government Gazette entries capture official notices including company registrations, name changes, land transfers, and government appointments. Trove also provides access to the PANDORA web archive (archived Australian websites).

### Australian Government Web Archive (AGWA)
- **URL:** https://webarchive.nla.gov.au/collection/gov
- **What it provides:** Archived Australian government websites. Captures government web content that may have been removed or changed with changes of government, machinery of government changes, or policy shifts.
- **Access:** Free.
- **Tips:** Useful for finding government program pages, policy documents, and grant scheme details that have been taken down. If a company's government contract or grant was once promoted on a department website, the archived version may still be accessible.

### Wayback Machine
- **URL:** https://web.archive.org
- **What it provides:** Historical snapshots of websites worldwide. Shows how a website appeared at different points in time. Captures deleted pages, removed content, and changed claims.
- **Access:** Free.
- **Tips:** Compare the target company's website over time — look for removed team members, changed claims, deleted pages, and evolving messaging. The CDX API (https://web.archive.org/cdx/search/cdx) enables programmatic searching of all archived URLs for a domain. Check robots.txt history to see if the company has tried to block archiving. Sitemap archaeology — compare sitemaps over time to identify pages that have been removed. The "Changes" view compares two snapshots side by side.

---

## 12. Industry-Specific News Sources

### Smart Company
- **URL:** https://www.smartcompany.com.au
- **What it provides:** News and analysis covering Australian small and medium businesses, startups, and entrepreneurs. Covers funding rounds, business growth stories, regulatory changes, and sector analysis.
- **Access:** Free. Some premium content.
- **Tips:** Good for coverage of mid-market and growing companies that may not appear in mainstream business media. The startup coverage is particularly strong.

### Business News Australia
- **URL:** https://www.businessnewsaustralia.com
- **What it provides:** Australian business news with strong coverage of the Brisbane and Queensland market, plus national stories. Lists and rankings (e.g., fastest growing companies, top startups).
- **Access:** Free. Some content behind registration.
- **Tips:** The lists and rankings are useful for benchmarking. Regional coverage fills gaps left by Sydney/Melbourne-centric outlets.

### Inside Small Business
- **URL:** https://insidesmallbusiness.com.au
- **What it provides:** News and resources for Australian small businesses. Covers regulatory changes, technology, and business management.
- **Access:** Free.

### The Mandarin
- **URL:** https://www.themandarin.com.au
- **What it provides:** News and analysis focused on the Australian public sector — government policy, public service leadership, government technology, and the relationship between government and the private sector.
- **Access:** Free.
- **Tips:** Essential for understanding government context around a target company that works with government. Covers machinery of government changes, senior public service appointments, and policy shifts that affect government procurement and service delivery.

### Pro Bono Australia (News)
- **URL:** https://probonoaustralia.com.au/news/
- **What it provides:** The primary news source for the Australian NFP and social enterprise sector. Covers policy, funding, leadership changes, sector trends, and organisational news.
- **Access:** Free.
- **Tips:** If the target is a charity, social enterprise, or NFP, Pro Bono Australia will likely have coverage that mainstream media does not. Search for the organisation name and key people.

### Ethical Jobs
- **URL:** https://www.ethicaljobs.com.au
- **What it provides:** Job board for the NFP, social enterprise, and ethical business sector. Job listings reveal organisational structure, salary ranges, strategic direction, and culture.
- **Access:** Free.
- **Tips:** Search for current and past job listings from the target organisation. Job descriptions reveal internal structure, reporting lines, project priorities, and salary ranges. The types of roles being advertised signal growth areas or capability gaps.

### Whirlpool
- **URL:** https://whirlpool.net.au
- **What it provides:** Australia's largest broadband and technology community forum. Extensive user discussions about ISPs, technology companies, financial institutions, and service providers.
- **Access:** Free.
- **Tips:** Search the forums for the company name. Whirlpool discussions are unfiltered customer/user experiences and opinions. Particularly strong for telecommunications, banking, and technology companies. Forum threads can reveal service issues, billing disputes, and company responses that never appear in mainstream media.

### ProductReview.com.au
- **URL:** https://www.productreview.com.au
- **What it provides:** Australian consumer review platform covering products, services, and businesses. Star ratings, written reviews, and company responses.
- **Access:** Free.
- **Tips:** Check for the target company's listing and read reviews. Look for patterns in complaints rather than individual reviews. Company responses (or lack thereof) indicate how they handle customer feedback. The "Verified Purchaser" tag adds credibility to reviews.

---

## 13. Social Procurement Framework Reference

### Victorian Government Social Procurement Framework (SPF)
- **URL:** https://www.buyingfor.vic.gov.au/social-procurement-framework
- **What it provides:** Mandatory social procurement framework for all Victorian Government procurement. Defines social and sustainable procurement objectives, direct sourcing rules, and reporting requirements.
- **Key rules:**
  - Direct sourcing from social enterprises and Aboriginal businesses permitted under $100,000 (goods/services) and $200,000 (construction) without competitive quotation.
  - All procurement over $20 million must include social procurement commitments.
  - Seven SPF objectives: opportunities for Victorian Aboriginal people, women, disadvantaged Victorians, people with disability; sustainable Victorian regions and social enterprises; environmentally sustainable business practices; safe and fair workplaces.
- **Access:** Free. All guidance and templates published online.
- **Tips:** Understanding the SPF is critical for assessing social enterprise revenue opportunities in Victoria. Social Traders certification aligns directly with the SPF social enterprise objective. Check whether the target organisation is leveraging SPF opportunities and whether it holds relevant certifications.

### NSW Social Procurement Policy
- **URL:** https://info.buy.nsw.gov.au (search for "social procurement")
- **What it provides:** NSW Government's approach to social procurement. Less prescriptive than Victoria's SPF but includes guidelines for considering social outcomes in procurement.
- **Key features:**
  - Social Procurement Policy Statement guiding agencies to consider social benefit.
  - Aboriginal Procurement Policy (APP) with mandatory targets for procurement from Aboriginal businesses.
  - Small and Medium Enterprise (SME) procurement targets.
- **Access:** Free.
- **Tips:** NSW's Aboriginal Procurement Policy sets specific targets for government spending with Aboriginal businesses — relevant for Supply Nation certified entities. The SME procurement policy also creates opportunities for smaller suppliers.

### Queensland Social Enterprise & Jobs Plan
- **URL:** https://desbt.qld.gov.au (search for "social enterprise")
- **What it provides:** Queensland Government's strategy for growing the social enterprise sector, including procurement commitments and support programs.
- **Key features:**
  - Queensland Social Enterprise Strategy supports growth of the sector.
  - Queensland Procurement Policy includes a focus on local and social benefit.
  - Buy Queensland approach emphasises ethical supply chains and social outcomes.
- **Access:** Free.

### Federal Commonwealth Procurement Rules (CPRs)
- **URL:** https://www.finance.gov.au/government/procurement/commonwealth-procurement-rules
- **What it provides:** The rules governing all federal government procurement. Includes provisions for considering social value in procurement evaluations.
- **Key features:**
  - Value for money is the core principle (not lowest price).
  - Evaluation criteria can include environmental sustainability, social benefit, and Indigenous participation.
  - Indigenous Procurement Policy (IPP) sets mandatory targets for Commonwealth contracts with Indigenous businesses.
  - Exemptions and limited tender provisions allow direct engagement in certain circumstances.
- **Access:** Free.
- **Tips:** The CPRs allow for social value to be included as evaluation criteria. The Indigenous Procurement Policy (IPP) sets a mandatory target of 3% of Commonwealth contracts (by number and value) with Indigenous businesses. The Advancing Procurement Connected to Indigenous Capability (APIC) requirement applies to contracts in certain regions and above certain values.

### Local Government Social Procurement Policies
- **What they provide:** Many local councils have adopted their own social procurement policies, particularly in Victoria (where it aligns with the state SPF) and increasingly in other states.
- **Access:** Free — check individual council websites.
- **Tips:** Local government is a significant procurement market for social enterprises. Policies vary widely — some councils have dedicated social procurement officers and specific targets, while others have aspirational policies without teeth. Check the specific council websites in the target organisation's area of operation. Victorian councils are generally the most advanced due to the mandatory state SPF.

---

## Quick Reference: The Original 8 Sources

These are the foundational sources embedded in the company-intel skill from the outset:

| # | Source | URL | Primary Use |
|---|--------|-----|-------------|
| 1 | ABN Lookup | abr.business.gov.au | Entity identity, ABN, GST status |
| 2 | ASIC | asic.gov.au | Company registration, directors, shareholders |
| 3 | ACNC | acnc.gov.au | Charity details, financials, responsible persons |
| 4 | IP Australia | ipaustralia.gov.au | Trademarks and patents |
| 5 | GrantConnect | grants.gov.au | Federal government grants |
| 6 | AusTender | tenders.gov.au | Federal procurement contracts |
| 7 | Social Traders | socialtraders.com.au | Social enterprise directory |
| 8 | Wayback Machine | web.archive.org | Historical website snapshots |

---

## Source Selection by Investigation Phase

A quick guide to which sources are most relevant at each phase of a company-intel investigation:

| Phase | Primary Sources | Secondary Sources |
|-------|----------------|-------------------|
| **Phase 1: Identification** | ABN Lookup, ASIC, ACNC | ORIC (if Indigenous corp) |
| **Phase 5: Financial & Legal** | ASIC Documents, ACNC, PPSR, AusTender, GrantConnect, AustLII, Credit services | AFSA, ASIC Published Notices, State tender portals |
| **Phase 6: People** | ASIC (directors), ACNC (responsible persons), AHPRA, AFSL Register | ASIC Banned & Disqualified, Professional registers |
| **Phase 8: Digital Footprint** | Wayback Machine, DNS tools | AGWA |
| **Phase 9: Customers & Stakeholders** | AusTender, GrantConnect, State tenders, Social Traders, Supply Nation | Council DA registers, NPI |
| **Phase 10: Industry & Market** | Industry news sources, Social procurement frameworks | AEC Transparency, Lobbyist registers |
| **Synthesis / QA** | AustLII (court check), Hansard, ACCC, Trove | Royal Commission transcripts, Ombudsman reports |

---

## Sector-to-Register Quick Reference

When you know the sector but not which register to check, use this table:

| Sector | Primary register | Secondary register |
|---|---|---|
| For-profit company | ASIC (companies register) | ABR (trading names, GST status) |
| Charity / NFP | ACNC (if DGR or registered charity) | ASIC (if incorporated) |
| Indigenous corporation | ORIC (Office of the Registrar of Indigenous Corporations) | ABR |
| Cooperative | State cooperatives register (varies by state) | ASIC (if national) |
| Trust | ABR (trustee ABN) | No central trust register exists in Australia |
| Government entity | Department website + AusTender | ABR |
| Social enterprise (unregistered) | Social Traders directory | ACNC (if NFP arm) |
| Financial services firm | ASIC financial services register | APRA (if licensed ADI or insurer) |
