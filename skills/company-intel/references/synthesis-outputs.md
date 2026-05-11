# Synthesis Output Templates

Reference document for Phase 11 (Synthesis) deliverables. Every investigation produces a purpose-specific synthesis assembled from these templates. Not all sections apply to every investigation — select based on the investigation purpose established in Phase 0.

---

## 1. RAG Dashboard (Always First Page)

Every synthesis begins with a one-page traffic-light summary. This is the single most important page — it gives the reader an instant assessment before they read anything else.

Save as the opening section of `00-summary/synthesis.md`.

```
RAG ASSESSMENT DASHBOARD
═══════════════════════════════════════════════════
Area                    │ Rating │ Key Finding
────────────────────────┼────────┼──────────────────
Financial Health        │ R/A/G  │ [one-line summary]
Revenue Quality         │ R/A/G  │ [one-line summary]
Leadership & People     │ R/A/G  │ [one-line summary]
Customer Concentration  │ R/A/G  │ [one-line summary]
Market Position         │ R/A/G  │ [one-line summary]
Regulatory & Compliance │ R/A/G  │ [one-line summary]
Technology & Digital    │ R/A/G  │ [one-line summary]
Reputation             │ R/A/G  │ [one-line summary]
ESG & Sustainability   │ R/A/G  │ [one-line summary]
Overall Assessment      │ R/A/G  │ [one-line summary]
═══════════════════════════════════════════════════
```

### Rating Criteria

**GREEN** — No material concerns. Evidence is positive or neutral across independent sources. No action required; monitor as normal.

**AMBER** — Concerns present but manageable. Mixed evidence, information gaps in important areas, or early warning signals detected. Requires attention and further monitoring. Flag specific conditions that would escalate to RED.

**RED** — Material risk or confirmed negative finding. Strong evidence of problems from multiple independent sources. Requires immediate attention, may be a deal-breaker depending on context. State the specific risk clearly.

### Area-Specific Rating Guidelines

| Area | GREEN | AMBER | RED |
|------|-------|-------|-----|
| Financial Health | Profitable or well-funded, growing revenue, clean audit | Marginal profitability, high debt, qualified audit opinion | Losses accelerating, solvency concerns, going concern qualification |
| Revenue Quality | Diversified customers, recurring revenue, growing | Moderate concentration, project-based, flat | Single-customer dependency, declining, contract disputes |
| Leadership & People | Stable team, strong track records, depth | Recent turnover in 1-2 key roles, thin bench | CEO/founder departure, serial failures in director history, key person risk |
| Customer Concentration | Top customer <15% of revenue | Top customer 15-40% of revenue | Top customer >40% of revenue |
| Market Position | Market leader or strong niche, growing share | Defensible position but competitive pressure increasing | Losing share, commoditised offering, disruption threat |
| Regulatory & Compliance | Clean record, proactive compliance | Minor infractions, pending matters, sector under review | Enforcement action, licence at risk, systemic compliance failures |
| Technology & Digital | Modern stack, digital-first, good reviews | Legacy systems but functional, digital transformation underway | Critical tech debt, no digital presence, security incidents |
| Reputation | Positive media, strong employer brand, good reviews | Mixed reviews, some negative coverage, historical issues addressed | Active negative media, unresolved complaints, trust deficit |
| ESG & Sustainability | Published framework, measurable progress, industry leader | Commitments stated but evidence thin, industry average | Greenwashing indicators, environmental incidents, labour issues |
| Overall Assessment | Weighted summary considering investigation purpose — which areas matter most for this specific decision |

### Weighting by Investigation Purpose

- **Acquisition:** Financial Health and Revenue Quality carry double weight
- **Investment:** Financial Health, Market Position, and Leadership carry double weight
- **Partnership:** Reputation, Leadership, and Regulatory carry double weight
- **Competitor analysis:** Market Position, Technology, and Revenue Quality carry double weight
- **Sales pursuit:** Financial Health (can they pay?), Leadership (who decides?), and Technology (do they need us?) carry double weight
- **Social enterprise:** Financial Health, ESG, and Revenue Quality carry double weight

---

## 2. Critical Findings Section (After RAG Dashboard)

The 5-7 most decision-relevant findings. This is the "if you read only one more page" section. Follows immediately after the RAG Dashboard.

```
CRITICAL FINDINGS
═════════════════

1. [Finding stated in one sentence]
   Confidence: ★★★/★★/★/⚠  |  Detail: Section [X]
   Implication: [What this means for the decision at hand]

2. [Finding stated in one sentence]
   Confidence: ★★★/★★/★/⚠  |  Detail: Section [X]
   Implication: [What this means for the decision at hand]

3. [Finding stated in one sentence]
   Confidence: ★★★/★★/★/⚠  |  Detail: Section [X]
   Implication: [What this means for the decision at hand]

4. [Finding stated in one sentence]
   Confidence: ★★★/★★/★/⚠  |  Detail: Section [X]
   Implication: [What this means for the decision at hand]

5. [Finding stated in one sentence]
   Confidence: ★★★/★★/★/⚠  |  Detail: Section [X]
   Implication: [What this means for the decision at hand]
```

### Selection Criteria for Critical Findings

Include a finding here if it meets ANY of these tests:
- It could change the decision (go/no-go, bid/no-bid, engage/avoid)
- It was unexpected and reframes the picture
- It has a time-sensitive element (window closing, trigger event approaching)
- It represents a material risk not visible from public positioning
- It contradicts the target's own narrative

Order findings by decision-relevance, not by topic.

---

## 3. Executive Summary

Structure depends on the investigation purpose established in Phase 0. Each purpose has a different information hierarchy because different decisions require different emphasis.

### Acquisition Executive Summary

```
EXECUTIVE SUMMARY — ACQUISITION ASSESSMENT
═══════════════════════════════════════════

Target:          [Company name]
Sector:          [Industry/sector]
Jurisdiction:    [Primary operating jurisdiction]
Assessment date: [Date]
Assessor:        [Name/org]

VALUATION-RELEVANT FACTORS
- Revenue: [amount, trend, quality assessment]
- EBITDA/margin: [amount, trajectory, sustainability]
- Key assets: [IP, contracts, customer relationships, property]
- Key liabilities: [debt, contingent liabilities, pending claims]

REVENUE QUALITY
- Recurring vs project-based: [ratio]
- Customer concentration: [top 5 customers as % of revenue]
- Contract visibility: [backlog, pipeline, renewal rates]
- Revenue recognition: [any concerns with timing/method]

MARGIN TRAJECTORY
- Gross margin trend: [3-year if available]
- Cost structure: [fixed vs variable, scalability]
- Wage dependency: [labour cost as % of revenue]

DEAL-BREAKERS IDENTIFIED
- [List any RED items from RAG dashboard that cannot be mitigated]
- [Or state: "No deal-breakers identified — proceed to detailed due diligence"]

INTEGRATION CONSIDERATIONS
- Technology: [compatibility, migration complexity]
- People: [key retention targets, cultural alignment, redundancy risk]
- Customers: [overlap, conflict, retention risk post-acquisition]
- Regulatory: [approvals needed, FIRB, ACCC, sector-specific]
```

### Investment Executive Summary

```
EXECUTIVE SUMMARY — INVESTMENT SCREENING
═════════════════════════════════════════

Target:          [Company name]
Stage:           [Seed/Series A/B/C/Growth/Mature]
Sector:          [Industry/sector]
Assessment date: [Date]

GROWTH TRAJECTORY
- Revenue CAGR: [X% over Y years]
- Customer/user growth: [metric and trend]
- Market expansion: [geographic, product, segment]
- Scalability evidence: [margin improvement at scale]

CASH GENERATION
- Operating cash flow: [positive/negative, trend]
- Capital requirements: [capex intensity, funding runway]
- Path to profitability: [timeline, credibility of plan]

RISK-ADJUSTED RETURNS
- Key upside drivers: [2-3 factors]
- Key downside risks: [2-3 factors]
- Risk mitigation: [what protections exist]

EXIT SCENARIOS
- Strategic acquirers: [likely buyers and rationale]
- IPO potential: [market, timing, comparables]
- Secondary sale: [liquidity options]
- Timeline: [expected hold period]
```

### Partnership Executive Summary

```
EXECUTIVE SUMMARY — PARTNERSHIP ASSESSMENT
══════════════════════════════════════════

Target:          [Company name]
Partnership type: [JV/Reseller/Referral/Co-delivery/Strategic alliance]
Assessment date: [Date]

STRATEGIC FIT
- Complementary capabilities: [what they have that we need, and vice versa]
- Market access: [what markets/customers this opens]
- Strategic alignment: [shared goals, compatible strategies]

CULTURAL COMPATIBILITY
- Decision-making style: [evidence from org structure, leadership, Glassdoor]
- Values alignment: [stated values vs evidence of practice]
- Working style indicators: [size, pace, formality, geographic spread]

REPUTATIONAL RISK
- Association risk: [any negative coverage, regulatory issues, controversies]
- Brand alignment: [how their brand perception maps to ours]

MUTUAL BENEFIT
- What they gain: [our capabilities/access they likely need]
- What we gain: [their capabilities/access we need]
- Power balance: [who needs whom more — affects negotiation dynamics]
```

### Competitor Executive Summary

```
EXECUTIVE SUMMARY — COMPETITIVE INTELLIGENCE
═════════════════════════════════════════════

Target:          [Competitor name]
Assessment date: [Date]
Threat level:    [HIGH/MEDIUM/LOW — with rationale]

COMPETITIVE THREAT ASSESSMENT
- Direct overlap: [products/services where you compete head-to-head]
- Trajectory: [are they moving toward or away from your space?]
- Win/loss indicators: [any evidence of deals won/lost against them]

MARKET OVERLAP
- Geographic: [where you compete]
- Segment: [which customer segments]
- Product/service: [which offerings compete directly]

STRENGTHS TO COUNTER
- [Strength 1] — how to neutralise: [approach]
- [Strength 2] — how to neutralise: [approach]

VULNERABILITIES TO EXPLOIT
- [Weakness 1] — how to leverage: [approach]
- [Weakness 2] — how to leverage: [approach]
```

### Sales Prospect Executive Summary

```
EXECUTIVE SUMMARY — SALES PROSPECT INTELLIGENCE
════════════════════════════════════════════════

Target:          [Company name]
Assessment date: [Date]
Opportunity size: [Estimated — with basis for estimate]

BUYER PERSONA
- Company profile: [size, sector, growth stage, culture]
- Technology maturity: [current stack, digital sophistication]
- Procurement style: [formal tender, relationship-driven, committee-based]

BUDGET SIGNALS
- Financial health: [can they afford it — evidence]
- Recent spending: [technology/service procurement evidence]
- Budget cycle: [FY dates, planning window]

PAIN POINTS
- [Pain point 1] — evidence: [how we know] — our solution: [alignment]
- [Pain point 2] — evidence: [how we know] — our solution: [alignment]
- [Pain point 3] — evidence: [how we know] — our solution: [alignment]

DECISION-MAKING PROCESS
- Economic buyer: [who controls budget]
- Technical buyer: [who evaluates capability]
- Champion: [who is most likely to advocate internally]
- Blocker: [who might resist — and why]
- Process: [committee, sole decision-maker, tender board]
```

---

## 4. Purpose-Specific Executive Briefings

Standalone 1-2 page briefings tailored to the investigation purpose. These are designed to be shared independently of the full dossier.

### Sales Pursuit Brief

Save as `00-summary/sales-pursuit-brief.md`.

```
SALES PURSUIT BRIEF
════════════════════

TARGET OVERVIEW
Company:     [Name]
Sector:      [Industry]
Size:        [Employees / Revenue]
HQ:          [Location]
Website:     [URL]

DECISION-MAKERS
┌─────────────────┬──────────────┬───────────────────────────────────┐
│ Name            │ Title        │ Engagement Notes                  │
├─────────────────┼──────────────┼───────────────────────────────────┤
│ [Person 1]      │ [Title]      │ [Background, interests, style]    │
│ [Person 2]      │ [Title]      │ [Background, interests, style]    │
│ [Person 3]      │ [Title]      │ [Background, interests, style]    │
└─────────────────┴──────────────┴───────────────────────────────────┘

PAIN POINTS MAPPED TO OFFERINGS
Pain Point               │ Evidence                │ Our Solution
─────────────────────────┼─────────────────────────┼──────────────
[Pain 1]                 │ [How we know]           │ [Product/service]
[Pain 2]                 │ [How we know]           │ [Product/service]
[Pain 3]                 │ [How we know]           │ [Product/service]

COMPETITIVE LANDSCAPE FOR THIS DEAL
- Incumbent: [who they use now — evidence]
- Likely competitors: [who else will bid — evidence]
- Our differentiation: [specific to this target's needs]

RECOMMENDED APPROACH
- Entry point: [who to contact and how]
- Opening angle: [what to lead with]
- Timeline: [urgency factors]

RISKS
- [Risk 1 — and mitigation]
- [Risk 2 — and mitigation]
```

### Partnership Assessment Brief

Save as `00-summary/partnership-assessment.md`.

```
PARTNERSHIP ASSESSMENT
══════════════════════

STRATEGIC FIT ANALYSIS
Dimension              │ Assessment │ Evidence
───────────────────────┼────────────┼──────────────────
Market complementarity │ H/M/L      │ [evidence]
Capability gap fill    │ H/M/L      │ [evidence]
Strategic alignment    │ H/M/L      │ [evidence]
Brand compatibility    │ H/M/L      │ [evidence]
Geographic fit         │ H/M/L      │ [evidence]

CULTURAL COMPATIBILITY
Dimension              │ Them              │ Us                │ Compatibility
───────────────────────┼───────────────────┼───────────────────┼──────────────
Organisation size      │ [size]            │ [size]            │ H/M/L
Decision speed         │ [fast/med/slow]   │ [fast/med/slow]   │ H/M/L
Formality              │ [formal/informal] │ [formal/informal] │ H/M/L
Values emphasis        │ [stated values]   │ [stated values]   │ H/M/L

FINANCIAL HEALTH SUMMARY
- Revenue trend: [growing/stable/declining]
- Profitability: [profitable/breakeven/loss-making]
- Solvency: [any concerns]
- Implication for partnership: [can they invest in the partnership]

KEY PEOPLE TO ENGAGE
- [Person 1] — [why they matter for partnership]
- [Person 2] — [why they matter for partnership]

POTENTIAL DEAL STRUCTURES
- [Structure 1] — pros/cons
- [Structure 2] — pros/cons

RED FLAGS
- [Flag 1 — severity and implication]
- [Flag 2 — severity and implication]
- [Or: "No material red flags identified"]
```

### Competitive Response Brief

Save as `00-summary/competitive-response.md`.

```
COMPETITIVE RESPONSE BRIEF
═══════════════════════════

WHAT THEY ARE DOING
[2-3 sentences summarising the competitive move, product launch, market entry, or strategic shift]

WHY IT MATTERS
[2-3 sentences on the impact to our business, market position, or specific deals]

THEIR STRENGTHS TO COUNTER
Strength                    │ Our Counter
────────────────────────────┼──────────────────────────
[Strength 1]                │ [How to neutralise/reframe]
[Strength 2]                │ [How to neutralise/reframe]
[Strength 3]                │ [How to neutralise/reframe]

THEIR WEAKNESSES TO EXPLOIT
Weakness                    │ Our Opportunity
────────────────────────────┼──────────────────────────
[Weakness 1]                │ [How to leverage]
[Weakness 2]                │ [How to leverage]
[Weakness 3]                │ [How to leverage]

RECOMMENDED ACTIONS
Action                      │ Owner     │ Timeline
────────────────────────────┼───────────┼──────────
[Action 1]                  │ [team]    │ [by when]
[Action 2]                  │ [team]    │ [by when]
[Action 3]                  │ [team]    │ [by when]
```

### Investment Screening Memo

Save as `00-summary/investment-screening.md`.

```
INVESTMENT SCREENING MEMO
═════════════════════════

BUSINESS OVERVIEW
- Founded: [year]
- Headquarters: [location]
- Sector: [industry/sub-sector]
- Business model: [description in 2-3 sentences]
- Stage: [seed/growth/mature]

MARKET OPPORTUNITY
- TAM: [total addressable market — with source]
- SAM: [serviceable addressable market]
- Current market share: [estimate — with basis]
- Market growth rate: [with source]
- Tailwinds: [macro/sector trends supporting growth]
- Headwinds: [macro/sector trends creating risk]

TEAM ASSESSMENT
- Founder/CEO: [background, track record, domain expertise]
- Leadership team: [strength, gaps, bench depth]
- Board: [composition, relevant experience, investor representation]
- Key person risk: [assessment]

FINANCIAL SUMMARY
- Revenue: [amount, CAGR, quality]
- Margins: [gross, EBITDA/operating, trend]
- Cash position: [runway, burn rate if applicable]
- Capital structure: [debt, equity, preference terms]

KEY RISKS
1. [Risk — likelihood — impact — mitigation]
2. [Risk — likelihood — impact — mitigation]
3. [Risk — likelihood — impact — mitigation]

COMPARABLE TRANSACTIONS
Transaction              │ Date     │ Multiple │ Relevance
─────────────────────────┼──────────┼──────────┼──────────
[Comp 1]                 │ [date]   │ [xEV/Rev]│ [why relevant]
[Comp 2]                 │ [date]   │ [xEV/Rev]│ [why relevant]
[Comp 3]                 │ [date]   │ [xEV/Rev]│ [why relevant]

PRELIMINARY VALUATION INDICATORS
- Revenue multiple range: [X-Yx based on comparables]
- Implied valuation range: [$X-$Y]
- Key sensitivities: [what moves the needle most]
```

### Social Enterprise Assessment

Save as `00-summary/social-enterprise-assessment.md`.

```
SOCIAL ENTERPRISE ASSESSMENT
═════════════════════════════

ORGANISATION OVERVIEW
- Legal name: [name]
- ABN/ACN: [number]
- Legal structure: [company limited by guarantee / incorporated association / co-op / etc.]
- ACNC registered: [yes/no — charity subtype]
- DGR status: [yes/no — item number]
- Founded: [year]
- Location: [primary operations]
- Employees: [FTE count]
- Annual revenue: [amount — source]

SOCIAL ENTERPRISE TYPOLOGY
- Primary type: [employment / trading / hybrid / community enterprise]
- Beneficiary group: [who benefits from the social mission]
- Mission integration: [is the mission embedded in operations or funded by separate trading?]
- Social Traders certification: [yes/no/eligible]
- Supply Nation certified: [yes/no/eligible — if Indigenous-owned]

MISSION INTEGRITY ASSESSMENT
Dimension              │ Assessment │ Evidence
───────────────────────┼────────────┼──────────────────
Mission clarity        │ H/M/L      │ [evidence]
Mission-revenue link   │ H/M/L      │ [is revenue earned through mission delivery?]
Impact measurement     │ H/M/L      │ [do they measure and report outcomes?]
Governance alignment   │ H/M/L      │ [does governance protect mission?]
Asset lock             │ Y/N        │ [are assets locked to purpose?]

FINANCIAL SUSTAINABILITY
- Revenue mix: [% earned income / % grants / % donations / % government]
- Trend: [improving/stable/deteriorating]
- Reserves: [months of operating costs]
- Key financial risks: [dependency, concentration, grant cliffs]

BENEFICIARY IMPACT
- Number of beneficiaries: [direct count if available]
- Impact evidence: [what outcomes are documented]
- Impact measurement maturity: [anecdotal / outputs tracked / outcomes measured / independently evaluated]

SOCIAL PROCUREMENT READINESS
- Certifications held: [Social Traders, Supply Nation, B Corp, other]
- Government panel memberships: [any standing offers or panels]
- Past government contracts: [evidence from AusTender, state equivalents]
- Capability statement: [available / not available]
- Insurance and compliance: [appropriate for procurement scale]

REVENUE OPPORTUNITY ASSESSMENT
- Alignment with our needs: [what they can provide to us or our clients]
- Capability match: [H/M/L — with specific gaps noted]
- Capacity: [can they scale to meet demand?]
- Risk: [what could go wrong in engaging them?]
```

---

## 5. Engagement Playbook

For sales, BD, and partnership contexts. Save as `00-summary/engagement-playbook.md`.

### Recommended Approach Angle

The single strongest reason this company should talk to you, drawn directly from evidence uncovered during the investigation. Not a generic value proposition — a specific, evidence-based hook.

```
RECOMMENDED APPROACH ANGLE
═══════════════════════════
Primary hook: [The single most compelling reason to engage, tied to specific evidence]
Evidence base: [What you found that supports this angle]
Why now: [Time-sensitive element that creates urgency]
```

### Conversation Framework

```
CONVERSATION FRAMEWORK
══════════════════════

OPENING HOOK
[Reference something specific and recent — a conference talk, a published article,
a job posting that signals a strategic shift, a recent award. Show you have done
your homework without being creepy.]

Example: "I noticed [Company] recently posted three data engineering roles on Seek —
that's a significant investment. We've been helping [similar company] with exactly
that kind of scaling challenge..."

DISCOVERY QUESTIONS (tailored to their pain points)
1. [Question targeting Pain Point 1 — open-ended, shows domain expertise]
2. [Question targeting Pain Point 2 — connects to evidence found]
3. [Question about their strategic direction — based on observable signals]
4. [Question about current solution — diplomatic, non-threatening]
5. [Question about decision process — timing-appropriate, not premature]

VALUE ALIGNMENT STATEMENTS
- "We've seen companies in [their sector] facing [specific challenge]..." → connects to [our capability]
- "[Their stated priority from annual report/website] is exactly where..." → connects to [our capability]
- "The [regulatory/market change] affecting [their sector]..." → connects to [our capability]

OBJECTION PRE-EMPTION
Likely objection           │ Pre-emptive response
───────────────────────────┼──────────────────────────
[Objection 1 — e.g. "we   │ [Response — ideally with social proof
already have a provider"]  │  from their sector]
[Objection 2 — e.g. "not  │ [Response — tie to urgency signal
in our budget cycle"]      │  or business case framing]
[Objection 3 — e.g. "too  │ [Response — reference comparable
small/big for us"]         │  client wins]
```

### Stakeholder Engagement Sequence

```
STAKEHOLDER ENGAGEMENT SEQUENCE
════════════════════════════════

STEP 1: [Name / Title]
Why first: [They are the most accessible / most likely champion / gatekeeper]
Approach: [Channel — LinkedIn, email, warm intro, event]
Goal: [What you want from this conversation — information, internal referral, meeting]

STEP 2: [Name / Title]
Why second: [They control budget / have the pain point / are the technical evaluator]
Approach: [Channel — referral from Step 1, direct approach with context]
Goal: [What you want from this conversation]

STEP 3: [Name / Title]
Why third: [They are the decision-maker / sign-off authority]
Approach: [Should come via introduction from Step 1 or 2]
Goal: [Meeting to present proposal / discuss partnership]

ALTERNATIVE PATH (if Step 1 is unresponsive):
[Name / Title] — [approach and rationale]
```

### Landmine Map

```
LANDMINE MAP
════════════

TOPICS TO AVOID
- [Topic 1] — Why: [e.g. recent litigation, public embarrassment, failed project]
- [Topic 2] — Why: [e.g. known sensitivity, internal politics]

SENSITIVITIES
- [Sensitivity 1] — [context and evidence]
- [Sensitivity 2] — [context and evidence]

PREVIOUS BAD VENDOR EXPERIENCES
- [If discoverable — previous provider who damaged trust, and what went wrong]
- [Implication for how you should position reliability/trust]

VISIBLE INTERNAL POLITICS
- [Any evidence of faction, reorganisation, contested strategy]
- [Who is on which side, if discernible]
- [Implication for your engagement approach]
```

### Competitive Displacement Strategy

Include only when the target currently uses a competitor's product or service.

```
COMPETITIVE DISPLACEMENT STRATEGY
══════════════════════════════════

CURRENT INCUMBENT
Provider: [name]
Relationship length: [estimate — from evidence]
Known contract value: [if discoverable]
Contract renewal: [date if discoverable]

INCUMBENT'S KNOWN WEAKNESSES
- [Weakness 1] — evidence: [source]
- [Weakness 2] — evidence: [source]

SWITCHING COSTS
- Technical: [data migration, integration rework, retraining]
- Commercial: [contract lock-in, early termination, sunk costs]
- Relationship: [personal relationships, political capital spent on selection]
- Estimated total switching friction: HIGH/MEDIUM/LOW

TRIGGER FOR CHANGE
- [What event or condition would make them reconsider — e.g. contract renewal,
  leadership change, failed project, new strategic priority]
- [How close are they to that trigger — evidence]

DISPLACEMENT APPROACH
- [How to position against incumbent without directly attacking]
- [Wedge offering — small, low-risk initial engagement that demonstrates value]
- [Expand strategy — how to grow from wedge to full displacement]
```

---

## 6. Competitive Battle Cards

Save individual cards to `00-summary/battle-cards/[competitor-name].md`.

```
BATTLE CARD: [Your Company] vs [Competitor X]
═════════════════════════════════════════════

Last updated: [date]
Context: [specific deal/market/segment this card addresses]

WHERE WE WIN
- [Capability 1] — evidence: [target's stated need or competitor's known gap]
- [Capability 2] — evidence: [target's stated need or competitor's known gap]
- [Capability 3] — evidence: [target's stated need or competitor's known gap]

WHERE THEY WIN
- [Capability 1] — mitigation: [how to reframe or neutralise]
- [Capability 2] — mitigation: [how to reframe or neutralise]

THEIR LIKELY PITCH
- [What they will emphasise about themselves]
- [What narrative they will construct]
- [What proof points they will use]

LANDMINES THEY WILL PLANT
- [What they will say about you — specific FUD tactics]
- [What doubts they will try to create]

COUNTER-NARRATIVES
- "If they say [X], respond with [Y] — because [evidence/logic]"
- "If they say [X], respond with [Y] — because [evidence/logic]"
- "If they say [X], respond with [Y] — because [evidence/logic]"

PRICE POSITIONING
- Their likely price range: [from public data, job ads, case studies, Glassdoor]
- Their pricing model: [per user, per project, retainer, outcome-based]
- How to justify premium: [if we are more expensive — value framing]
- How to compete on value: [if we are similar price — differentiation framing]

PROOF POINTS TO DEPLOY
- [Case study / reference / metric that directly counters their strongest claim]
- [Case study / reference / metric relevant to this target's specific context]

WIN/LOSS INTELLIGENCE
- [Any known wins against this competitor — what worked]
- [Any known losses to this competitor — what happened]
```

---

## 7. Buying Signal Register

Save as part of `00-summary/engagement-playbook.md` or standalone in `00-summary/buying-signals.md`.

```
BUYING SIGNAL REGISTER
═══════════════════════════════════════════════════════════════════════
Signal                        │ Type       │ Strength │ Window   │ Source
──────────────────────────────┼────────────┼──────────┼──────────┼────────
[e.g. New CTO appointed]     │ Leadership │ HIGH     │ Now-90d  │ LinkedIn ★★
[e.g. 3 data engineer roles] │ Pain       │ MEDIUM   │ Ongoing  │ Seek ★★
[e.g. Series B closed]       │ Funding    │ HIGH     │ Now-180d │ AFR ★★★
[e.g. "Digital transformation│ Strategic  │ MEDIUM   │ FY27     │ Annual Report ★★
 priority" in annual report] │            │          │          │
[e.g. Mentioned legacy system │ Pain       │ HIGH     │ Now-90d  │ Conference talk ★★
 challenges at conference]   │            │          │          │
[e.g. Incumbent contract     │ Contract   │ HIGH     │ Q3 2026  │ AusTender ★★★
 expires Sep 2026]           │ Expiry     │          │          │
═══════════════════════════════════════════════════════════════════════
```

### Signal Types

- **Growth** — Expansion, new markets, hiring, funding, acquisition
- **Leadership** — New C-suite, new board members, restructure
- **Funding** — Capital raise, grant received, new investor
- **Strategic** — Published strategy shift, new partnerships, pivot
- **Pain** — Hiring for missing capability, negative reviews, public complaints, failed project
- **Contract Expiry** — Known end-date of existing supplier agreement

### Strength Assessment

- **HIGH** — Multiple confirming signals, time-sensitive, directly relevant to your offering
- **MEDIUM** — Single signal, relevant but not urgent, may need further validation
- **LOW** — Indirect signal, speculative interpretation, useful as conversation starter only

---

## 8. Timing Intelligence

Save as part of `00-summary/engagement-playbook.md`.

```
TIMING INTELLIGENCE
═══════════════════

Financial year:     [e.g. 1 Jul - 30 Jun]
Budget planning:    [e.g. Feb-Apr — approach by January for FY27 inclusion]
Best outreach:      [window and specific rationale — e.g. "Oct-Nov: post-Q1 results,
                     budget underspend decisions being made"]
Avoid:              [window and specific rationale — e.g. "Jun-Jul: EOFY crunch and
                     new FY onboarding, low decision-making bandwidth"]
Next board meeting: [estimated — based on quarterly reporting pattern or evidence]
Industry peak:      [season and relevance — e.g. "Retail: avoid Nov-Jan peak trading"]
Trigger event:      [specific event and closing window — e.g. "New CTO starts 15 Mar,
                     90-day window for vendor reviews typically follows"]

RECOMMENDED TIMING
══════════════════
[Specific recommendation with rationale — e.g. "Initiate contact week of 20 October.
This gives 2 weeks post-Q1 results for the new CFO to settle in, lands before
November budget lock, and aligns with the job postings suggesting active investment
in data capability."]
```

---

## 9. Introduction Pathways

Save as part of `00-summary/engagement-playbook.md`.

```
INTRODUCTION PATHWAYS
═════════════════════

Path 1 (Strength: HIGH)
You → [Your contact: Name at Org X] → [Intermediary: Name, role] → [Target: Name, Title at Target Co]
Evidence: [How you identified this connection — e.g. "both spoke at same conference",
"previously worked together at Company Z per LinkedIn", "share board membership at NFP Y"]
Ask: [Specific request — "Could you introduce me to [Target] regarding [topic]?"]

Path 2 (Strength: MEDIUM)
You → [Your contact: Name, Client Y] → [Y's former colleague who worked at Target]
Evidence: [e.g. "LinkedIn shows [name] worked at [Target] 2019-2023 as [role]"]
Ask: [Specific request — "Could you connect me with [name] for background on [Target]?"]

Path 3 (Strength: LOW)
You → [Cold approach via LinkedIn/email with contextual hook]
Evidence: [What makes this approach viable — e.g. "They actively engage on LinkedIn,
recently commented on [topic] which aligns with our offering"]
Ask: [Specific, low-commitment request — insight, not a sales meeting]

NO PATHWAY FOUND
[If no introduction paths exist, state this explicitly and recommend cold approach
strategy with the strongest available contextual hooks]
```

### Strength Criteria

- **HIGH** — Direct mutual contact who has an active relationship with the target person
- **MEDIUM** — Second-degree connection, or contact has historical (not current) relationship
- **LOW** — Shared community/affiliation but no direct relationship evidence

---

## 10. Vulnerability Assessment

Distinct from the RAG Dashboard risk flags. This section is specifically for competitive contexts — where you are competing against this company for business, talent, or market position.

Save as `00-summary/vulnerability-assessment.md` (for competitor investigations).

```
VULNERABILITY ASSESSMENT
════════════════════════

KEY PERSON DEPENDENCY
- [Person] — [role and why they are critical]
- Risk if departed: [impact assessment]
- Evidence: [how we know this person is critical — e.g. named on all patents,
  sole client relationship holder, only person with [skill]]

CUSTOMER CONCENTRATION
- Top customer: [name if discoverable, otherwise sector] — [% of revenue]
- Risk: [what happens if this customer leaves]
- Evidence: [source — ASIC filings, case studies, job ads mentioning client name]

TECHNOLOGY DEBT
- [Evidence of legacy systems — e.g. job ads seeking COBOL skills, Wayback Machine
  showing unchanged website for years, reviews mentioning outdated tools]
- Risk: [inability to innovate, high maintenance costs, security vulnerabilities]

TALENT GAPS
- [Roles they cannot seem to fill — evidence from long-running job ads]
- [Skills they lack — evidence from project failures, outsourcing patterns]
- [Glassdoor/SEEK reviews indicating cultural issues affecting retention]

REPUTATIONAL VULNERABILITY
- [Negative media that could resurface]
- [Customer complaints on public forums]
- [Regulatory actions or investigations]
- [ESG controversies]

FINANCIAL PRESSURE POINTS
- [Debt maturity dates]
- [Grant cliff — major grant funding ending]
- [Customer contract renewals clustered in one period]
- [Seasonal cash flow vulnerability]

STRATEGIC BLIND SPOTS
- [Markets they are ignoring that you can capture]
- [Customer segments underserved]
- [Technology trends they appear to be missing]
```

---

## 11. Scenario Analysis

Include in every synthesis. Save as a section within `00-summary/synthesis.md`.

```
SCENARIO ANALYSIS
═════════════════

BULL CASE (Probability: [X]%)
Conditions required:
- [Condition 1]
- [Condition 2]
- [Condition 3]
Estimated outcome: [What this means for the decision — acquisition price, deal size,
partnership value, competitive threat level]
Key indicators to watch: [What would confirm this scenario is unfolding]

BASE CASE (Probability: [X]%)
Conditions required:
- [Condition 1]
- [Condition 2]
- [Condition 3]
Estimated outcome: [What this means for the decision]
Key indicators to watch: [What would confirm this scenario is unfolding]

BEAR CASE (Probability: [X]%)
Conditions required:
- [Condition 1]
- [Condition 2]
- [Condition 3]
Estimated outcome: [What this means for the decision]
Key indicators to watch: [What would confirm this scenario is unfolding]

PROBABILITIES MUST SUM TO 100%
```

### Scenario Construction Rules

- Each scenario must be internally consistent (conditions must logically produce the outcome)
- Base case should reflect the most likely trajectory based on current evidence
- Bull and bear cases should represent plausible extremes, not fantasy
- Probability assignments must be justified by evidence, not gut feel
- Identify the 1-2 variables that determine which scenario unfolds (these become monitoring priorities)

---

## Monitoring Plan

Template lives in `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §11. Use that template exactly.

**company-intel extension — standard alert terms to include:**
| Alert term | Why |
|---|---|
| "[Company name]" | Core monitoring |
| "[Company name]" insolvency OR liquidation OR administration | Financial distress |
| "[Key person name]" | Key actor monitoring |
| "[Company name]" ASIC OR court OR tribunal | Regulatory/legal |
| "[Company name]" site:acnc.gov.au | Charity register updates (if NFP) |

---

## Assumptions and Limitations

Template lives in `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §12. Use that template exactly.

**company-intel extension — standard limitations to always note:**
- ACNC financial statements have a 12–18 month publication lag
- LinkedIn data obtained without authentication — completeness cannot be verified
- ABR/ASIC data is current as of the date of the API call; historical changes require manual ASIC search
- Glassdoor and employer review data is self-selected and may not be representative

---

## 14. Key Questions for Management

If the reader gets a meeting with target leadership, these are the 10 most important questions to ask — derived from what the research revealed and what it could not resolve.

Save as `00-summary/management-questions.md`.

```
KEY QUESTIONS FOR MANAGEMENT
═════════════════════════════

These questions are designed for a face-to-face meeting with [Target Company] leadership.
They address the most significant information gaps and unresolved findings from this
investigation. Questions are ordered by priority.

 1. [Question targeting the single biggest information gap]
    Context: [Why this matters — what you found and what is missing]
    What a good answer looks like: [Benchmark for evaluating their response]
    Red flag answer: [What would concern you]

 2. [Question targeting a contradictory finding]
    Context: [The contradiction you found]
    What a good answer looks like: [Expected explanation if benign]
    Red flag answer: [What would confirm concern]

 3. [Question about revenue quality/sustainability]
    Context: [What the data shows and what is uncertain]

 4. [Question about leadership/team stability]
    Context: [What is known and what is missing]

 5. [Question about competitive position]
    Context: [Market evidence and gaps]

 6. [Question about technology/operations]
    Context: [Signals detected and not verified]

 7. [Question about customer relationships]
    Context: [Concentration, satisfaction, retention]

 8. [Question about regulatory/compliance]
    Context: [Current status and upcoming changes]

 9. [Question about growth plans/strategy]
    Context: [Stated strategy vs evidence of execution]

10. [Question about the specific opportunity/deal]
    Context: [Directly relevant to the investigation purpose]
```

### Question Design Principles

- Each question should be open-ended (not yes/no)
- Each should reference specific evidence to show preparation depth
- Frame questions to reveal information, not to impress
- Include "Context" so the person asking understands why they are asking
- Include "good answer" and "red flag" guidance where possible so the questioner can evaluate in real-time

---

## Information Gaps Register

Template lives in `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §10. Use that template exactly.

**company-intel extension:** The following areas are most commonly gap-prone in company investigations:
- ASIC-registered charges and security interests (often not publicly searchable)
- Court and tribunal proceedings where the company is a defendant
- Beneficial ownership structures (trusts, nominee arrangements)
- Related-party transactions not disclosed in ACNC filings
- Historical ASIC deregistrations or name changes for key directors

Log all inaccessible sources to `inaccessible-sources.md` at the investigation root.

---

## 16. Revenue Discovery Outputs (Social Enterprise Crisis Mode)

For social enterprise targets facing financial sustainability challenges. Save to `11-revenue-opportunities/`.

### service-market-matching.md

```
SERVICE-MARKET MATCHING
═══════════════════════

CURRENT CAPABILITIES
Capability                │ Evidence          │ Capacity    │ Quality Evidence
──────────────────────────┼───────────────────┼─────────────┼─────────────────
[e.g. Grounds maintenance]│ [website, ACNC]   │ [X FTE]     │ [contracts held, reviews]
[e.g. Catering]           │ [website]         │ [X FTE]     │ [certifications, clients]

ADJACENT SERVICES (low development cost to add)
Adjacent Service          │ Based on Capability │ Development Needed │ Market Demand
──────────────────────────┼─────────────────────┼────────────────────┼─────────────
[e.g. Commercial cleaning]│ [Grounds maint.]   │ [Training + equip] │ [HIGH/MED/LOW]

SOCIAL PROCUREMENT DEMAND MAPPING
Buyer Type                │ Demand Area           │ Policy Driver         │ Accessibility
──────────────────────────┼───────────────────────┼───────────────────────┼─────────────
[State gov dept]          │ [Service category]    │ [Policy name/ref]     │ [Open/Panel/Tender]
[Local council]           │ [Service category]    │ [Social procurement   │ [Open/Panel/Tender]
                          │                       │  framework ref]       │
[Corporate]               │ [Service category]    │ [RAP/ESG commitment]  │ [Direct/RFQ]
```

### geographic-opportunities.md

```
GEOGRAPHIC OPPORTUNITIES
════════════════════════

LOCAL GOVERNMENTS WITH SOCIAL PROCUREMENT POLICIES
Council/LGA              │ Policy Name              │ Relevant Categories    │ Contact Point
─────────────────────────┼──────────────────────────┼────────────────────────┼──────────────
[Council 1]              │ [Policy ref]             │ [Services in scope]    │ [Procurement team]
[Council 2]              │ [Policy ref]             │ [Services in scope]    │ [Procurement team]

STATE DEPARTMENTS
Department               │ Social Procurement Target │ Relevant Panels        │ Next Opportunity
─────────────────────────┼───────────────────────────┼────────────────────────┼────────────────
[Department 1]           │ [% or $ target]           │ [Panel names]          │ [Estimated]

LOCAL CORPORATES WITH RAP/ESG COMMITMENTS
Company                  │ Commitment Type     │ Relevant Need           │ Approach
─────────────────────────┼─────────────────────┼─────────────────────────┼──────────
[Company 1]              │ [RAP / ESG / B Corp]│ [Service alignment]     │ [Contact]

UPCOMING INFRASTRUCTURE PROJECTS
Project                  │ Value     │ Stage      │ Social Procurement Req │ SE Opportunity
─────────────────────────┼───────────┼────────────┼────────────────────────┼──────────────
[Project 1]              │ [$X]      │ [Planning] │ [% or policy]          │ [Subcontract scope]
```

### peer-revenue-models.md

```
PEER REVENUE MODELS
═══════════════════

Peer 1: [Organisation Name]
- Type: [SE typology]
- Size: [revenue, FTE]
- Revenue model: [description]
- Revenue mix: [earned %] / [grants %] / [donations %] / [government %]
- Source: [ACNC AIS, annual report, website]
- Key difference from target: [what they do that the target does not]
- Transferable insight: [what the target could adopt]

Peer 2: [Organisation Name]
[same structure]

Peer 3: [Organisation Name]
[same structure]

REVENUE STREAMS THE TARGET LACKS
Stream                    │ Peer Evidence        │ Feasibility for Target │ Est. Revenue Potential
──────────────────────────┼──────────────────────┼────────────────────────┼───────────────────────
[e.g. Fee-for-service     │ [Peer 1 earns $Xk]  │ HIGH/MED/LOW           │ [$X - $Y annually]
 training]                │                      │                        │
```

### grant-pipeline.md

```
GRANT PIPELINE
══════════════

OPEN GRANTS (as at [date])
Grant Name               │ Funder              │ Amount     │ Closes    │ Eligibility Match │ Effort
─────────────────────────┼─────────────────────┼────────────┼───────────┼───────────────────┼───────
[Grant 1]                │ [GrantConnect/State] │ [$X-$Y]   │ [date]    │ HIGH/MED/LOW      │ H/M/L

UPCOMING GRANTS (known funding rounds)
Grant Name               │ Funder              │ Est. Amount│ Opens     │ Eligibility Match
─────────────────────────┼─────────────────────┼────────────┼───────────┼──────────────────
[Grant 1]                │ [Source]            │ [$X-$Y]   │ [est.]    │ HIGH/MED/LOW

DGR STATUS ASSESSMENT
- Current status: [DGR endorsed / not endorsed]
- If not endorsed: [Eligibility assessment — could they qualify? Under which item?]
- Revenue implication: [DGR status enables tax-deductible donations, workplace giving,
  corporate philanthropy — estimated additional revenue potential: $X-$Y]

PHILANTHROPIC TRUSTS AND FOUNDATIONS
Foundation               │ Focus Area          │ Typical Grant │ Application │ Fit
─────────────────────────┼─────────────────────┼───────────────┼─────────────┼────
[Foundation 1]           │ [Focus]             │ [$X-$Y]       │ [Open/EOI]  │ H/M/L
```

### quick-wins.md

```
QUICK WINS — REVENUE ACCELERATION
══════════════════════════════════

0-90 DAYS (existing capabilities, existing relationships, no new certifications)
Priority │ Action                              │ Revenue Est. │ Dependency     │ First Step
─────────┼─────────────────────────────────────┼──────────────┼────────────────┼──────────
1        │ [e.g. Approach Council X re grounds] │ [$X/yr]      │ [None]         │ [Call procurement]
2        │ [e.g. Apply for Grant Y]            │ [$X]         │ [DGR status]   │ [Check eligibility]
3        │ [e.g. List on Social Traders]       │ [Indirect]   │ [Application]  │ [Contact ST]

6-12 MONTHS (new certifications, new relationships, modest capability development)
Priority │ Action                              │ Revenue Est. │ Investment Req │ First Step
─────────┼─────────────────────────────────────┼──────────────┼────────────────┼──────────
1        │ [e.g. Obtain ISO certification]     │ [$X/yr]      │ [$Y + time]    │ [Identify provider]
2        │ [e.g. Develop fee-for-service arm]  │ [$X/yr]      │ [$Y + FTE]     │ [Business case]

12+ MONTHS (new markets, new capabilities, strategic investment)
Priority │ Action                              │ Revenue Est. │ Investment Req │ First Step
─────────┼─────────────────────────────────────┼──────────────┼────────────────┼──────────
1        │ [e.g. Enter commercial cleaning]    │ [$X/yr]      │ [$Y + FTE]     │ [Market research]
```

### crisis-stabilisation.md

```
CRISIS STABILISATION OPTIONS
═════════════════════════════

For organisations in immediate financial distress (less than 6 months cash runway).

EMERGENCY GRANTS
Grant/Fund               │ Amount    │ Timeline │ Application Effort │ Contact
─────────────────────────┼───────────┼──────────┼────────────────────┼────────
[Emergency fund 1]       │ [$X]      │ [X weeks]│ LOW                │ [Details]

SECTOR INTERMEDIARY SUPPORT
Organisation             │ Support Type              │ Cost    │ Contact
─────────────────────────┼───────────────────────────┼─────────┼────────
[e.g. Social Traders]    │ [Certification, brokerage]│ [Free/$]│ [Details]
[e.g. SEWN]              │ [Peer support, referrals] │ [Free]  │ [Details]
[e.g. State SE network]  │ [Mentoring, connections]  │ [Free]  │ [Details]

MERGER / PARTNERSHIP / AUSPICE OPPORTUNITIES
Option                   │ Partner Type       │ Benefit                    │ Risk
─────────────────────────┼────────────────────┼────────────────────────────┼──────
[Merge with similar SE]  │ [Complementary org]│ [Shared overheads, scale]  │ [Mission drift, governance]
[Auspice arrangement]    │ [Larger org]       │ [Reduced admin burden]     │ [Loss of independence]
[Strategic partnership]  │ [Corporate/gov]    │ [Guaranteed revenue]       │ [Dependency]

UNUSED ASSET CAPACITY
Asset                    │ Current Utilisation │ Potential Use              │ Revenue Estimate
─────────────────────────┼─────────────────────┼────────────────────────────┼─────────────────
[e.g. Commercial kitchen]│ [3 days/week]       │ [Hire out 2 days/week]     │ [$X/week]
[e.g. Training room]     │ [Mornings only]     │ [Afternoon hire]           │ [$X/week]
[e.g. Vehicle fleet]     │ [Weekdays only]     │ [Weekend hire/share]       │ [$X/week]
```

---

## 17. Triangulation Matrix Template

Enhanced with source independence assessment. Include in every synthesis. Save as a section within `00-summary/synthesis.md`.

```
TRIANGULATION MATRIX
═══════════════════════════════════════════════════════════════════════════════════
Finding          │ Source 1 (type) │ Source 2 (type) │ Source 3 (type) │ Confidence │ Independence
─────────────────┼─────────────────┼─────────────────┼─────────────────┼────────────┼─────────────
[finding text]   │ [source] (P)    │ [source] (Si)   │ [source] (Sd)   │ ★★★        │ HIGH
[finding text]   │ [source] (Sd)   │ [source] (Sd)   │ —               │ ★           │ LOW
[finding text]   │ [source] (P)    │ [source] (Si)   │ [source] (P)    │ ★★★        │ HIGH
[finding text]   │ [source] (P)    │ [source] (Sd)   │ [contradicts]   │ ⚠           │ —
═══════════════════════════════════════════════════════════════════════════════════
```

### Source Type Classification

| Code | Type | Description | Examples |
|------|------|-------------|----------|
| P | Primary | Official records, audited statements, court records, regulatory filings | ASIC filings, ACNC AIS, AusTender, court judgments, audited financials, ABR |
| Si | Secondary Independent | Independent journalism, analyst reports, academic research | Investigative journalism, independent analyst reports, academic papers, industry body reports |
| Sd | Secondary Dependent | Company's own claims, reprinted press releases, sponsored content | Company website, press releases, company blog, sponsored articles, paid case studies, company social media |

### Confidence Rating Rules

| Rating | Symbol | Criteria |
|--------|--------|----------|
| CONFIRMED | ★★★ | 2+ Primary sources, OR 1 Primary + 1 Secondary Independent |
| HIGH | ★★★ | 2+ Secondary Independent sources (no Primary available) |
| MEDIUM | ★★ | 1 Primary source only, OR 2+ Secondary Dependent sources |
| LOW | ★ | 1 Secondary Dependent source only |
| CONTESTED | ⚠ | Contradictory evidence across sources — apply Analysis of Competing Hypotheses (ACH) |

### Independence Assessment

| Rating | Criteria |
|--------|----------|
| HIGH | Sources have no editorial, financial, or organisational relationship to each other or the target |
| MEDIUM | Some sources may share upstream information (e.g. both journalists citing the same press release) |
| LOW | Sources are editorially dependent (e.g. press release reprinted verbatim across outlets) |

### When Sources Contradict (⚠)

Apply Analysis of Competing Hypotheses (ACH):
1. List all possible explanations for the contradictory evidence
2. For each explanation, assess which sources it is consistent with and which it contradicts
3. The explanation that is inconsistent with the fewest sources is the most likely
4. Document the analysis explicitly — do not silently choose one source over another

---

## 18. Confirmation Bias Safeguards

Mandatory "Devil's Advocate" check before finalising any synthesis. This is a quality gate — do not skip it.

Save as a section within `00-summary/synthesis.md`, immediately before the final recommendation.

```
CONFIRMATION BIAS CHECK
════════════════════════

CENTRAL NARRATIVE
[State the primary thesis/conclusion of this investigation in 1-2 sentences]

EVIDENCE CONTRADICTING THE CENTRAL NARRATIVE
1. [Contradictory finding 1] — Source: [source] — Significance: [why this matters]
2. [Contradictory finding 2] — Source: [source] — Significance: [why this matters]
3. [Contradictory finding 3] — Source: [source] — Significance: [why this matters]

INVERSION TEST
For each of the 3 strongest positive claims in this synthesis:

Claim 1: [State the positive claim]
Inverted: "What if [the opposite] were true?"
Evidence for the inversion: [What evidence, if any, supports the opposite conclusion?]
Assessment: [Does the inversion hold? If partially, how does it modify the claim?]

Claim 2: [State the positive claim]
Inverted: "What if [the opposite] were true?"
Evidence for the inversion: [What evidence, if any, supports the opposite conclusion?]
Assessment: [Does the inversion hold? If partially, how does it modify the claim?]

Claim 3: [State the positive claim]
Inverted: "What if [the opposite] were true?"
Evidence for the inversion: [What evidence, if any, supports the opposite conclusion?]
Assessment: [Does the inversion hold? If partially, how does it modify the claim?]

NARRATIVE ADJUSTMENT
[Based on the Devil's Advocate check, does the central narrative need to be softened,
qualified, or changed? State any adjustments here. If the narrative holds, state why
the contradictory evidence does not change the conclusion.]

ANALYST CONFIDENCE
After conducting this check, overall confidence in the central narrative is:
[CONFIRMED / HIGH / MODERATE / LOW — with brief explanation]
```

### When to Intensify Bias Checking

Apply additional scrutiny (e.g. second pass, additional inversion tests) when:
- The investigation was commissioned with a strong prior expectation (e.g. "we want to acquire them")
- All evidence points uniformly in one direction (suspiciously clean picture)
- The target is skilled at narrative management (PR-heavy, limited independent coverage)
- Findings would support a large financial commitment

---

## Output Assembly Guide

Not all sections apply to every investigation. Use the investigation purpose from Phase 0 to select which sections to include.

### Always Include (every investigation)
1. RAG Dashboard
2. Critical Findings
3. Executive Summary (purpose-appropriate variant)
4. Scenario Analysis
5. Triangulation Matrix
6. Assumptions and Limitations
7. Confirmation Bias Safeguards
8. Information Gaps (Enhanced)
9. Monitoring Plan

### Include by Purpose

| Section | Acquisition | Investment | Partnership | Competitor | Sales | Social Enterprise |
|---------|:-----------:|:----------:|:-----------:|:----------:|:-----:|:-----------------:|
| Sales Pursuit Brief | | | | | X | |
| Partnership Assessment | | | X | | | |
| Competitive Response Brief | | | | X | | |
| Investment Screening Memo | X | X | | | | |
| Social Enterprise Assessment | | | | | | X |
| Engagement Playbook | | | X | | X | X |
| Battle Cards | | | | X | X | |
| Buying Signal Register | | | X | | X | |
| Timing Intelligence | X | X | X | | X | |
| Introduction Pathways | | | X | | X | X |
| Vulnerability Assessment | | | | X | | |
| Key Questions for Management | X | X | X | | X | X |
| Revenue Discovery Outputs | | | | | | X |

### File Structure

```
[company-name]/
├── 00-summary/
│   ├── synthesis.md                    ← Main document (RAG, Critical Findings, Exec Summary,
│   │                                     Scenarios, Triangulation, Assumptions, Bias Check, Gaps)
│   ├── engagement-playbook.md          ← Playbook, Buying Signals, Timing, Intro Pathways
│   ├── management-questions.md         ← Key Questions for Management
│   ├── monitoring-plan.md              ← Monitoring Plan
│   ├── sales-pursuit-brief.md          ← If sales purpose
│   ├── partnership-assessment.md       ← If partnership purpose
│   ├── competitive-response.md         ← If competitor purpose
│   ├── investment-screening.md         ← If investment/acquisition purpose
│   ├── social-enterprise-assessment.md ← If social enterprise purpose
│   ├── vulnerability-assessment.md     ← If competitor purpose
│   └── battle-cards/
│       └── [competitor-name].md        ← One per competitor
├── 01-corporate-structure/
├── 02-financials/
├── ...
└── 11-revenue-opportunities/           ← If social enterprise crisis mode
    ├── service-market-matching.md
    ├── geographic-opportunities.md
    ├── peer-revenue-models.md
    ├── grant-pipeline.md
    ├── quick-wins.md
    └── crisis-stabilisation.md
```
