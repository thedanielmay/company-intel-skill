# Analytical Frameworks Reference

Reference document for all analytical frameworks used within the company-intel skill. Each framework includes a description, template, key questions it answers, and "So What?" guidance connecting analysis to the user's decision.

Select frameworks based on the investigation purpose established in Phase 0. Every framework output in the final synthesis MUST include a "So What?" paragraph.

---

## Cross-Reference: Shared Analytical Standards

The following framework components live in the shared standards and should be applied from there, not redefined here:

| Component | Location |
|---|---|
| Triangulation Matrix | `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §7 |
| ACH (Analysis of Competing Hypotheses) | See §3 of this file (Contested Claims) — apply ACH format from IS.md §8 |
| Confirmation Bias / Devil's Advocate | `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §8 step 5 |
| KIT Answer Register | `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §3 |

Do not duplicate these templates here. Reference the shared document.

---

## 1. Business Strategy Frameworks

### 1.1 Porter's Five Forces

**What it is:** A framework for assessing the competitive intensity and attractiveness of an industry. Use it whenever the investigation involves market positioning, competitive dynamics, or industry entry/exit decisions.

**Key questions it answers:**
- How profitable is this industry likely to be?
- Where does the power sit — with buyers, suppliers, or incumbents?
- How defensible is the target's position?

**Template:**

```
PORTER'S FIVE FORCES — [Company / Industry]
════════════════════════════════════════════════════════════════
Force                        │ Rating │ Key Evidence
─────────────────────────────┼────────┼────────────────────────
Threat of New Entrants       │ H/M/L  │ [barriers, capital, regs]
Bargaining Power of Buyers   │ H/M/L  │ [concentration, switching]
Bargaining Power of Suppliers│ H/M/L  │ [alternatives, dependency]
Threat of Substitutes        │ H/M/L  │ [alternatives, price perf]
Competitive Rivalry          │ H/M/L  │ [number, growth, differ.]
════════════════════════════════════════════════════════════════
Overall Industry Attractiveness: [High / Medium / Low]
```

**Rating criteria:**
- **High** — this force significantly constrains profitability or strategic freedom
- **Medium** — this force is present and requires management but is not dominant
- **Low** — this force is weak; the target has freedom to operate

**So What? guidance:** Connect each force to the user's decision. For sales/BD: which forces create pain you can address? For due diligence: which forces threaten future margins? For competitive analysis: which forces could the target exploit or be exploited by?

---

### 1.2 Value Chain Analysis

**What it is:** Maps the sequence of activities through which the target creates and delivers value. Identifies where competitive advantage is generated and where vulnerabilities exist.

**Key questions it answers:**
- Where does the target create its differentiation?
- Which activities are performed in-house vs outsourced?
- Where are the cost centres and margin drivers?

**Template:**

```
VALUE CHAIN — [Company]
════════════════════════════════════════════════════════════════

PRIMARY ACTIVITIES
──────────────────
1. Inbound Logistics    │ [description] │ Advantage: Y/N │ [notes]
2. Operations           │ [description] │ Advantage: Y/N │ [notes]
3. Outbound Logistics   │ [description] │ Advantage: Y/N │ [notes]
4. Marketing & Sales    │ [description] │ Advantage: Y/N │ [notes]
5. Service              │ [description] │ Advantage: Y/N │ [notes]

SUPPORT ACTIVITIES
──────────────────
6. Firm Infrastructure  │ [description] │ Advantage: Y/N │ [notes]
7. Human Resources      │ [description] │ Advantage: Y/N │ [notes]
8. Technology Dev.      │ [description] │ Advantage: Y/N │ [notes]
9. Procurement          │ [description] │ Advantage: Y/N │ [notes]

KEY LINKAGES (where activities reinforce each other):
- [activity] ↔ [activity]: [how they connect]

COMPETITIVE ADVANTAGE SOURCE: [cost leadership / differentiation / focus]
VULNERABILITIES: [activities that are weak or outsourced to a single provider]
```

**So What? guidance:** For sales/BD: which activities are pain points you could solve? For due diligence: are the advantage-creating activities defensible and scalable? For partnership: where does your value chain complement theirs?

---

### 1.3 SWOT Analysis (Enhanced Action-Linked)

**What it is:** The standard Strengths-Weaknesses-Opportunities-Threats framework, enhanced so that every finding connects to a specific action or implication rather than sitting as a passive observation.

**Key questions it answers:**
- What are the target's internal advantages and disadvantages?
- What external factors could help or harm them?
- What should the user DO about each finding?

**Template:**

```
SWOT ANALYSIS — [Company]
════════════════════════════════════════════════════════════════

STRENGTHS (internal, positive)
──────────────────────────────
│ Finding              │ Evidence Source   │ Action / Implication     │
│ [strength]           │ [source, ★ rating]│ [what this means for you]│

WEAKNESSES (internal, negative)
───────────────────────────────
│ Finding              │ Evidence Source   │ Action / Implication     │
│ [weakness]           │ [source, ★ rating]│ [what this means for you]│

OPPORTUNITIES (external, positive)
──────────────────────────────────
│ Finding              │ Evidence Source   │ Action / Implication     │
│ [opportunity]        │ [source, ★ rating]│ [what this means for you]│

THREATS (external, negative)
────────────────────────────
│ Finding              │ Evidence Source   │ Action / Implication     │
│ [threat]             │ [source, ★ rating]│ [what this means for you]│

STRATEGIC COMBINATIONS:
- S+O: [strength that can exploit an opportunity]
- W+T: [weakness that a threat could exploit — highest risk]
- S+T: [strength that can defend against a threat]
- W+O: [opportunity that could address a weakness]
```

**So What? guidance:** The "Strategic Combinations" section is the most valuable part. S+O combinations indicate where the target can grow. W+T combinations are the danger zones. For sales: W+T and W+O are your entry points. For due diligence: W+T combinations are your risk factors.

---

### 1.4 PESTLE Analysis

**What it is:** Macro-environment assessment across six dimensions. Use when the target operates in a heavily regulated, politically sensitive, or rapidly changing environment.

**Key questions it answers:**
- What external forces shape this company's operating environment?
- Which macro trends are tailwinds vs headwinds?

**Template:**

```
PESTLE ANALYSIS — [Company / Industry]
════════════════════════════════════════════════════════════════
Factor       │ Current State    │ Trend (↑↓→) │ Impact on Target
─────────────┼──────────────────┼─────────────┼─────────────────
Political    │ [description]    │ [direction] │ [positive/negative]
Economic     │ [description]    │ [direction] │ [positive/negative]
Social       │ [description]    │ [direction] │ [positive/negative]
Technological│ [description]    │ [direction] │ [positive/negative]
Legal        │ [description]    │ [direction] │ [positive/negative]
Environmental│ [description]    │ [direction] │ [positive/negative]
════════════════════════════════════════════════════════════════
Top 3 macro factors for this target: [ranked by impact]
```

**So What? guidance:** Identify the 2-3 macro factors most likely to affect the target's trajectory over the user's time horizon. Connect each to a specific scenario or decision point.

---

### 1.5 Business Model Canvas

**What it is:** A one-page map of how the target creates, delivers, and captures value. Use for understanding the target's business model holistically.

**Key questions it answers:**
- How does this company make money?
- What are the critical dependencies in the model?
- Where is the model vulnerable?

**Template:**

```
BUSINESS MODEL CANVAS — [Company]
════════════════════════════════════════════════════════════════
Key Partners       │ Key Activities      │ Value Propositions
[who they depend   │ [what they do that  │ [why customers
on externally]     │ matters most]       │ choose them]
                   │                     │
                   │ Key Resources       │ Customer Relationships
                   │ [assets, IP, people │ [how they acquire,
                   │ that are critical]  │ retain, grow]
                   │                     │
───────────────────┴─────────────────────┼───────────────────
Cost Structure                           │ Revenue Streams
[biggest cost drivers, fixed vs variable]│ [how money comes in]
═══════════════════════════════════════════════════════════════
Channels: [how they reach customers]
Customer Segments: [who they serve]
```

**So What? guidance:** Look for single points of failure (one key partner, one channel, one revenue stream). For sales: understanding their value proposition reveals what they care about most. For due diligence: revenue stream diversity and cost structure flexibility indicate resilience.

---

### 1.6 Ansoff Matrix

**What it is:** Classifies growth strategy along two dimensions: market (existing vs new) and product/service (existing vs new). Use to assess the target's growth trajectory and associated risk.

**Template:**

```
ANSOFF MATRIX — [Company]
════════════════════════════════════════
                │ Existing Products │ New Products
────────────────┼───────────────────┼──────────────
Existing Markets│ MARKET PENETRATION│ PRODUCT DEV.
                │ [evidence]        │ [evidence]
────────────────┼───────────────────┼──────────────
New Markets     │ MARKET DEVELOPMENT│ DIVERSIFICATION
                │ [evidence]        │ [evidence]
════════════════════════════════════════
Current strategy: [which quadrant(s) the target is pursuing]
Risk level:      [penetration=lowest → diversification=highest]
```

**So What? guidance:** Companies pursuing diversification carry the most strategic risk. Penetration strategies are lowest risk but may signal a mature market. The quadrant(s) tell you where management attention and capital are going.

---

### 1.7 McKinsey 7S Framework

**What it is:** Assesses organisational alignment across seven interdependent elements. Use when evaluating organisational health, integration risk, or change readiness.

**Key questions it answers:**
- Is this organisation internally aligned?
- Where are the misalignments that create friction or risk?

**Template:**

```
McKINSEY 7S — [Company]
════════════════════════════════════════════════════════════════
Element       │ Assessment          │ Alignment │ Evidence
──────────────┼─────────────────────┼───────────┼──────────────
Strategy      │ [stated strategy]   │ ✓/✗/~     │ [source]
Structure     │ [org design]        │ ✓/✗/~     │ [source]
Systems       │ [processes, IT]     │ ✓/✗/~     │ [source]
Shared Values │ [culture, mission]  │ ✓/✗/~     │ [source]
Style         │ [leadership style]  │ ✓/✗/~     │ [source]
Staff         │ [people, talent]    │ ✓/✗/~     │ [source]
Skills        │ [capabilities]      │ ✓/✗/~     │ [source]
════════════════════════════════════════════════════════════════
Key Misalignments: [which elements are pulling in different directions]
Implication: [what the misalignment means for the target's ability to execute]
```

**So What? guidance:** Misalignment between Strategy and Structure/Systems is the most common source of execution failure. For acquisitions: misalignment between Shared Values and Style predicts integration difficulty. For partnerships: look at Systems and Skills alignment with your own organisation.

---

## 2. Intelligence Analysis Frameworks

### 2.1 Analysis of Competing Hypotheses (ACH)

**What it is:** A structured methodology developed by the CIA for evaluating contradictory evidence and avoiding confirmation bias. This is the primary tool for resolving ambiguous or conflicting findings in the investigation. It forces consideration of all plausible explanations before selecting the most likely one.

**When to use:** Any time two or more pieces of evidence contradict each other. Any time a key finding could have multiple explanations. Any time the analyst feels strongly that one explanation is correct — that is precisely when ACH is most needed.

**Key questions it answers:**
- Which hypothesis is best supported by the evidence?
- Which evidence is most diagnostic (i.e. helps distinguish between hypotheses)?
- Am I being misled by confirmation bias?

**Process:**

1. **Generate hypotheses** — list ALL plausible explanations, including ones you consider unlikely. Force yourself to include at least one you find uncomfortable.
2. **List evidence** — every relevant piece of evidence, including absence of expected evidence.
3. **Build the matrix** — for each piece of evidence, assess whether it is Consistent (C), Inconsistent (I), or Neutral (N) with each hypothesis.
4. **Assess diagnosticity** — evidence that is consistent with ALL hypotheses is useless. The most valuable evidence is that which is consistent with one hypothesis and inconsistent with others.
5. **Eliminate** — the hypothesis with the MOST inconsistent evidence is rejected first. Do NOT select the hypothesis with the most consistent evidence (that leads to confirmation bias).
6. **Sensitivity check** — if you removed any single piece of evidence, would the conclusion change? If yes, your conclusion rests on thin ground.

**Template:**

```
ANALYSIS OF COMPETING HYPOTHESES
═══════════════════════════════════════════════════════════════════
Question: [What are we trying to determine?]

Hypotheses:
  H1: [description]
  H2: [description]
  H3: [description]

Evidence Matrix:
──────────────────────────────────┬──────┬──────┬──────┬──────────
Evidence Item              Source │  H1  │  H2  │  H3  │ Diagnostic?
──────────────────────────────────┼──────┼──────┼──────┼──────────
E1: [evidence]            [src]  │  C   │  I   │  N   │ HIGH
E2: [evidence]            [src]  │  C   │  C   │  C   │ LOW
E3: [evidence]            [src]  │  I   │  C   │  I   │ HIGH
E4: [absent evidence]     [n/a]  │  I   │  C   │  N   │ MEDIUM
──────────────────────────────────┴──────┴──────┴──────┴──────────
C = Consistent   I = Inconsistent   N = Neutral

Inconsistency count:        H1: [n]   H2: [n]   H3: [n]
Most likely hypothesis:     [Hx — the one with FEWEST inconsistencies]
Confidence:                 [High/Medium/Low]
Sensitivity:                [Would removing any single evidence change the result?]

Key diagnostic evidence:    [The 1-2 pieces that most differentiate hypotheses]
Information gaps:           [Evidence that would resolve remaining ambiguity]
═══════════════════════════════════════════════════════════════════
```

**So What? guidance:** State the practical implication of the most likely hypothesis. If confidence is Low, recommend what additional information would resolve it. Flag if the conclusion depends on a single piece of evidence — that is a fragile finding.

---

### 2.2 Key Assumptions Check (KAC)

**What it is:** A structured method for surfacing and testing the assumptions underpinning a conclusion. Assumptions are the silent load-bearing structures of any analysis — if one fails, the whole finding collapses.

**When to use:** Before finalising any key finding in the synthesis. Particularly important for forward-looking assessments and scenario analysis.

**Template:**

```
KEY ASSUMPTIONS CHECK — [Finding or Assessment]
════════════════════════════════════════════════════════════════
Finding: [The conclusion being tested]

Assumption                │ Confidence │ If Wrong, Impact │ How to Test
──────────────────────────┼────────────┼──────────────────┼──────────────
[assumption 1]            │ H/M/L      │ [what breaks]    │ [verification]
[assumption 2]            │ H/M/L      │ [what breaks]    │ [verification]
[assumption 3]            │ H/M/L      │ [what breaks]    │ [verification]
════════════════════════════════════════════════════════════════
Load-bearing assumptions: [which ones, if wrong, invalidate the finding]
Recommended actions:      [test the load-bearing assumptions first]
```

**So What? guidance:** Any finding that rests on a Low-confidence, high-impact assumption should be flagged as tentative in the synthesis. Include the assumption explicitly so the reader knows what would change the conclusion.

---

### 2.3 Timeline Analysis

**What it is:** Chronological mapping of all significant events relating to the target, drawn from across all research phases. Placing events on a single timeline reveals patterns, correlations, and anomalies invisible when evidence is siloed by phase.

**When to use:** Always. Build the timeline incrementally as research progresses. Analyse it formally in Phase 11.

**Template:**

```
TIMELINE — [Company]
════════════════════════════════════════════════════════════════
Date       │ Event                    │ Source   │ Category  │ Signal
───────────┼──────────────────────────┼──────────┼───────────┼────────
YYYY-MM-DD │ [event description]      │ [source] │ [type]    │ [+/-/~]
YYYY-MM-DD │ [event description]      │ [source] │ [type]    │ [+/-/~]
════════════════════════════════════════════════════════════════

Categories: Corporate, Financial, People, Legal, Product, Media, Market
Signal: + (positive) / - (negative) / ~ (neutral or ambiguous)

PATTERN ANALYSIS:
- Clusters:    [events that bunch together — what triggered the cluster?]
- Sequences:   [A consistently follows B — is this causal?]
- Gaps:        [periods with no events — dormancy, secrecy, or data gap?]
- Inflections: [moments where trajectory changed — what caused the turn?]
```

**So What? guidance:** The most valuable output is inflection points — moments where the company's trajectory changed. Understanding what caused past inflections helps predict future ones. Clusters of negative events around structural changes (see "Shedding Skin" technique in investigative-methods.md) are a strong warning signal.

---

## Devil's Advocate Protocol

**Full template:** See `~/.claude/skills/shared/references/INTELLIGENCE-STANDARDS.md` §8 step 5.

**When to apply:** Before finalising any synthesis. Mandatory for Full Investigation tier.

**company-intel focus areas:**
- Financial performance: what explains results without assuming management competence?
- Leadership narrative: what do *critics* of this team say, and where is their evidence?
- Customer relationships: are positive references the full picture, or are there churned customers with different stories?
- Market position claims: are these from the company's own materials, or independently verified?

The goal is not to be contrarian but to stress-test the central narrative before it reaches the reader.

---

## 3. Financial Analysis Frameworks

### 3.1 Revenue Decomposition

**What it is:** Breaking total revenue into its component parts to understand quality, sustainability, and concentration risk. Revenue is not a single number — its composition determines how reliable it is.

**When to use:** Phase 5 (Financial), Phase 11 synthesis for any investigation involving financial assessment.

**Key questions it answers:**
- Where does the money actually come from?
- How reliable and repeatable is this revenue?
- What happens if the largest source disappears?

**Template:**

```
REVENUE DECOMPOSITION — [Company] — [Period]
════════════════════════════════════════════════════════════════

BY CUSTOMER (top 5 + remainder)
────────────────────────────────
Customer              │ Revenue ($) │ % of Total │ Trend  │ Contract?
──────────────────────┼─────────────┼────────────┼────────┼──────────
[customer 1]          │ [amount]    │ [%]        │ ↑↓→    │ Y/N [term]
[customer 2]          │ [amount]    │ [%]        │ ↑↓→    │ Y/N [term]
All others            │ [amount]    │ [%]        │ ↑↓→    │
──────────────────────┴─────────────┴────────────┴────────┴──────────

BY PRODUCT / SERVICE LINE
─────────────────────────
Line                  │ Revenue ($) │ % of Total │ Margin │ Trend
──────────────────────┼─────────────┼────────────┼────────┼──────
[product/service 1]   │ [amount]    │ [%]        │ [%]    │ ↑↓→
[product/service 2]   │ [amount]    │ [%]        │ [%]    │ ↑↓→

BY TYPE
───────
Recurring (subscriptions, retainers, contracts)   │ $[amount] │ [%]
Repeat (same customers, not contracted)            │ $[amount] │ [%]
One-off (project, transactional)                   │ $[amount] │ [%]
Grant / philanthropic (if applicable)              │ $[amount] │ [%]

BY GEOGRAPHY
────────────
[region 1]  │ $[amount] │ [%]
[region 2]  │ $[amount] │ [%]

BY CUSTOMER COHORT
──────────────────
New customers (this period)       │ $[amount] │ [%]
Existing customers (retained)     │ $[amount] │ [%]
Returning customers (re-acquired) │ $[amount] │ [%]
Churned (lost from prior period)  │ $[amount] │ [%]
════════════════════════════════════════════════════════════════
Net Revenue Retention Rate: [%]
Revenue Concentration (HHI): [index]
```

**So What? guidance:** High recurring revenue percentage with low customer concentration = high quality. Heavy reliance on one-off project revenue or a single customer = fragile. For acquisitions, recurring revenue commands a premium multiple. For sales, understanding the revenue mix tells you what they value (growth? stability? margin?).

---

### 3.2 Revenue Sustainability Scorecard

**What it is:** A traffic-light assessment of revenue quality across six dimensions. Produces a single-page view of how likely current revenue levels are to be maintained or grown.

**Template:**

```
REVENUE SUSTAINABILITY SCORECARD — [Company]
════════════════════════════════════════════════════════════════
Dimension              │ Rating │ Evidence                │ Score
───────────────────────┼────────┼─────────────────────────┼──────
Recurring Revenue %    │ R/A/G  │ [% recurring, trend]    │ /10
Concentration Risk     │ R/A/G  │ [top customer %, HHI]   │ /10
Diversification        │ R/A/G  │ [products, markets, geo] │ /10
Pricing Power          │ R/A/G  │ [ability to raise prices]│ /10
Competitive Moat       │ R/A/G  │ [switching costs, IP]   │ /10
Contract Visibility    │ R/A/G  │ [forward book, pipeline] │ /10
════════════════════════════════════════════════════════════════
Composite Score: [x]/60
Rating:         [Strong / Adequate / Vulnerable / Critical]

Rating thresholds:
  GREEN:  Recurring >60%, top customer <15%, 3+ products/markets, strong moat
  AMBER:  Recurring 30-60%, top customer 15-25%, some diversification
  RED:    Recurring <30%, top customer >25%, narrow offering, no moat
```

**So What? guidance:** A RED composite rating means revenue is fragile — any single shock (customer loss, competitor move, policy change) could materially damage the business. For acquisitions, discount the valuation. For sales, the target may be risk-averse and seeking stability. For partnerships, ensure you are not building dependency on a fragile partner.

---

### 3.3 Common-Size Financial Statements

**What it is:** Express every line item as a percentage of revenue, enabling comparison across time periods and against industry benchmarks regardless of absolute size.

**Template:**

```
COMMON-SIZE P&L — [Company]
════════════════════════════════════════════════════
Line Item              │ FY[n-2] │ FY[n-1] │ FY[n] │ Industry
───────────────────────┼─────────┼─────────┼───────┼─────────
Revenue                │ 100.0%  │ 100.0%  │ 100.0%│ 100.0%
COGS                   │ [%]     │ [%]     │ [%]   │ [%]
Gross Profit           │ [%]     │ [%]     │ [%]   │ [%]
───────────────────────┼─────────┼─────────┼───────┼─────────
Employee Costs         │ [%]     │ [%]     │ [%]   │ [%]
Marketing/Sales        │ [%]     │ [%]     │ [%]   │ [%]
Occupancy              │ [%]     │ [%]     │ [%]   │ [%]
Technology             │ [%]     │ [%]     │ [%]   │ [%]
Admin/Other            │ [%]     │ [%]     │ [%]   │ [%]
───────────────────────┼─────────┼─────────┼───────┼─────────
EBITDA                 │ [%]     │ [%]     │ [%]   │ [%]
D&A                    │ [%]     │ [%]     │ [%]   │ [%]
EBIT                   │ [%]     │ [%]     │ [%]   │ [%]
Interest               │ [%]     │ [%]     │ [%]   │ [%]
Tax                    │ [%]     │ [%]     │ [%]   │ [%]
Net Profit             │ [%]     │ [%]     │ [%]   │ [%]
════════════════════════════════════════════════════

TRENDS TO FLAG:
- Gross margin movement: [expanding / compressing / stable]
- Employee cost ratio: [increasing faster than revenue?]
- EBITDA margin trajectory: [direction and why]
```

**So What? guidance:** Gross margin compression over time signals pricing pressure or cost inflation. Employee costs rising as a percentage of revenue without corresponding revenue acceleration indicates scaling problems. Comparison to industry benchmarks reveals whether the target is more or less efficient than peers.

---

### 3.4 Unit Economics Estimation

**What it is:** Estimating the economics of acquiring and serving a single customer, even when the company does not publish these figures. Requires creative triangulation from available data.

**Key questions it answers:**
- Does each customer generate more value than they cost to acquire?
- How long until a customer becomes profitable?
- Is the business model fundamentally sound at the unit level?

**Template:**

```
UNIT ECONOMICS (ESTIMATED) — [Company]
════════════════════════════════════════════════════
Metric                     │ Estimate   │ Confidence │ Source
───────────────────────────┼────────────┼────────────┼────────
Total Customers            │ [number]   │ [★ rating] │ [src]
Revenue per Customer       │ $[amount]  │ [★ rating] │ [src]
Gross Margin per Customer  │ $[amount]  │ [★ rating] │ [derived]
───────────────────────────┼────────────┼────────────┼────────
CAC (Customer Acq. Cost)   │ $[amount]  │ [★ rating] │ [est.]
  — Marketing spend / new customers acquired
LTV (Lifetime Value)       │ $[amount]  │ [★ rating] │ [est.]
  — Avg revenue × gross margin × avg lifespan
LTV:CAC Ratio              │ [x]:1      │            │
Payback Period (months)    │ [months]   │            │
Contribution Margin        │ [%]        │            │
════════════════════════════════════════════════════
Estimation methodology: [explain how each figure was derived]

Health indicators:
  LTV:CAC > 3:1 = healthy
  LTV:CAC 1-3:1 = marginal
  LTV:CAC < 1:1 = unsustainable
  Payback < 12 months = strong
  Payback > 18 months = concern
```

**So What? guidance:** Unit economics below break-even mean the company loses money on every customer — growth makes things worse, not better. Even rough estimates with low confidence are valuable: if LTV:CAC is below 1:1 even with generous assumptions, the model has a structural problem.

---

### 3.5 Normalised Earnings / Adjusted EBITDA

**What it is:** Stripping out one-off, non-recurring, and non-operational items to reveal the true underlying earning power of the business. Critical for any valuation or acquisition assessment.

**Key questions it answers:**
- What does this business actually earn on a recurring basis?
- Are reported profits inflated or deflated by one-offs?
- What would earnings look like under a new owner?

**Template:**

```
NORMALISED EARNINGS — [Company] — [Period]
════════════════════════════════════════════════════
                                        │ Amount ($)
────────────────────────────────────────┼───────────
Reported Net Profit / (Loss)            │ [amount]
────────────────────────────────────────┼───────────
ADD BACK (non-recurring / non-operating)│
  One-off legal costs                   │ +[amount]
  Restructuring charges                 │ +[amount]
  Asset write-downs / impairments       │ +[amount]
  Gain/loss on asset disposal           │ ±[amount]
  Related-party adjustments *           │ ±[amount]
  Owner salary above market rate *      │ +[amount]
  Discretionary owner expenses          │ +[amount]
  Below-market rent (related party)     │ -[amount]
────────────────────────────────────────┼───────────
NORMALISED EBITDA                       │ [amount]
════════════════════════════════════════════════════

* Related-party adjustments: [detail each — above/below market rent,
  management fees to related entities, loans to/from directors]

* Owner adjustments: [detail — replace owner salary with market-rate
  CEO, remove personal expenses run through the business]

Adjustment confidence: [how confident are we in each adjustment?]
```

**So What? guidance:** The gap between reported and normalised earnings tells you how much the numbers are distorted by one-offs or owner behaviour. A large positive gap (normalised >> reported) may indicate hidden value. A large negative gap (normalised << reported) means reported profits are overstated. For acquisitions, normalised EBITDA is the starting point for valuation.

---

### 3.6 Working Capital Analysis

**What it is:** Assessing the cash conversion efficiency and liquidity of the business through receivables, inventory, and payables metrics.

**Template:**

```
WORKING CAPITAL ANALYSIS — [Company]
════════════════════════════════════════════════════════════════
Metric                      │ FY[n-2] │ FY[n-1] │ FY[n] │ Industry
────────────────────────────┼─────────┼─────────┼───────┼─────────
DSO (Days Sales Outstanding)│ [days]  │ [days]  │ [days]│ [days]
DIO (Days Inventory O/S)    │ [days]  │ [days]  │ [days]│ [days]
DPO (Days Payable O/S)      │ [days]  │ [days]  │ [days]│ [days]
Cash Conversion Cycle       │ [days]  │ [days]  │ [days]│ [days]
  (DSO + DIO - DPO)
────────────────────────────┼─────────┼─────────┼───────┼─────────
Current Ratio               │ [x]     │ [x]     │ [x]  │ [x]
Quick Ratio                 │ [x]     │ [x]     │ [x]  │ [x]
Free Cash Flow              │ $[amt]  │ $[amt]  │ $[amt]│
Cash Runway (months)        │ [n]     │ [n]     │ [n]  │
════════════════════════════════════════════════════════════════

SIGNALS:
- DSO increasing: customers paying slower — credit risk or disputes?
- DPO increasing: stretching suppliers — cash pressure or negotiating power?
- Cash conversion cycle lengthening: more cash trapped in operations
- Current ratio < 1.0: may not meet short-term obligations
- Cash runway < 6 months: material going-concern risk
```

**So What? guidance:** A lengthening cash conversion cycle alongside growing revenue means the company needs more working capital to fund growth — they may need external capital or will hit a cash crunch. For acquisitions, working capital requirements directly affect the deal's capital needs. Short cash runway (<6 months) is a RED flag that should appear on the RAG Dashboard.

---

## 4. Risk Assessment Frameworks

### 4.1 Key Person Dependency (KPD) Matrix

**What it is:** Assessment of how dependent the organisation is on specific individuals. High key-person risk is one of the most common deal-breakers in acquisitions and a major vulnerability for any organisation.

**Template:**

```
KEY PERSON DEPENDENCY MATRIX — [Company]
════════════════════════════════════════════════════════════════════
Person         │ Controls        │ Knowledge   │ Succession │ Flight │ Impact
               │                 │ Concentration│ Ready?    │ Risk   │ if Gone
───────────────┼─────────────────┼─────────────┼───────────┼────────┼────────
[Name, Role]   │ [relationships, │ H/M/L       │ Y/N/Partial│ H/M/L │ R/A/G
               │  IP, decisions] │             │            │        │
[Name, Role]   │ [relationships, │ H/M/L       │ Y/N/Partial│ H/M/L │ R/A/G
               │  IP, decisions] │             │            │        │
════════════════════════════════════════════════════════════════════

"Controls" includes: client relationships, supplier relationships,
  IP/technical knowledge, regulatory approvals, board relationships,
  community trust (for SEs), grant relationships, brand identity

Impact Rating:
  RED:    Business would not survive 6 months without this person
  AMBER:  Significant disruption for 6-12 months, recoverable
  GREEN:  Replaceable within normal business continuity processes

OVERALL KEY PERSON RISK: [Critical / High / Moderate / Low]
```

**So What? guidance:** A company with two or more RED-rated key persons is structurally fragile regardless of financial performance. For acquisitions: key person risk requires retention mechanisms (earnouts, lock-ins, deferred consideration). For sales: identify who the actual decision-maker is and whether they are also a key person (they usually are). For social enterprises: founder-dependency is extremely common and often under-recognised by the board.

---

### 4.2 Customer Concentration Heat Map

**What it is:** A visual risk assessment of revenue dependency on individual customers.

**Template:**

```
CUSTOMER CONCENTRATION HEAT MAP — [Company]
════════════════════════════════════════════════════════════════
Customer          │ % Revenue │ Risk Zone │ Contract │ Relationship │ Risk
──────────────────┼───────────┼───────────┼──────────┼──────────────┼──────
[Customer 1]      │ [%]       │ R/A/G     │ [term]   │ [key person] │ [notes]
[Customer 2]      │ [%]       │ R/A/G     │ [term]   │ [key person] │ [notes]
[Customer 3]      │ [%]       │ R/A/G     │ [term]   │ [key person] │ [notes]
[Customer 4]      │ [%]       │ R/A/G     │ [term]   │ [key person] │ [notes]
[Customer 5]      │ [%]       │ R/A/G     │ [term]   │ [key person] │ [notes]
[All others]      │ [%]       │           │          │              │
════════════════════════════════════════════════════════════════
Risk Zones:  RED >25% │ AMBER 15-25% │ GREEN <15%

Top-1 concentration:   [%]
Top-3 concentration:   [%]
Top-5 concentration:   [%]
HHI (Herfindahl):      [index]

Compound risk: [Does the key person who owns the client relationship
               also appear as a RED in the KPD Matrix? If yes, flag.]
```

**So What? guidance:** Customer concentration is one of the most reliable predictors of business fragility. A company where the top customer represents >40% of revenue is effectively a subcontractor to that customer, regardless of how it presents itself. For acquisitions: customer concentration directly reduces the valuation multiple. For sales: if the target depends on a single customer, their buying behaviour is driven by that customer's needs.

---

### 4.3 Deal-Breaker Checklist

**What it is:** A structured checklist of potential deal-breaking findings, organised by category. Each item includes an escalation trigger that defines when a finding crosses from "concern" to "deal-breaker."

**Template:**

```
DEAL-BREAKER CHECKLIST — [Company]
════════════════════════════════════════════════════════════════

FINANCIAL
─────────
□ Insolvency risk (current ratio <0.5, cash runway <3 months)
  Escalation: Any two financial distress indicators simultaneously → STOP
□ Fraud indicators (unexplained related-party transactions, revenue
  recognition anomalies, material undisclosed liabilities)
  Escalation: Any confirmed fraud indicator → STOP
□ Material misstatement (qualified audit, restated accounts)
  Escalation: Going concern qualification → STOP
□ Undisclosed debt or guarantees
  Escalation: Material debt not in accounts → FLAG

PEOPLE
──────
□ Key person imminent departure or non-compete conflict
  Escalation: Founder/CEO departure within 6 months of deal → STOP
□ Team instability (>40% leadership turnover in 12 months)
  Escalation: Multiple simultaneous C-suite departures → FLAG
□ Cultural red flags (Glassdoor <2.5, systemic complaints, legal claims)
  Escalation: Pattern of bullying/harassment complaints → FLAG

MARKET
──────
□ Declining market (>10% annual decline in addressable market)
  Escalation: Structural market decline with no pivot strategy → FLAG
□ Regulatory risk (pending regulation that could eliminate product/service)
  Escalation: Legislation in progress that would make business model illegal → STOP
□ Competitive disruption (well-funded competitor with superior offering)
  Escalation: Target losing >20% market share year-on-year → FLAG

GOVERNANCE
──────────
□ Related-party transactions (material, not at arm's length)
  Escalation: Undisclosed material related-party dealing → STOP
□ Compliance failures (regulatory sanctions, licence conditions breached)
  Escalation: Licence revocation or criminal prosecution → STOP
□ Board dysfunction (no independent directors, conflicts of interest)
  Escalation: Director disqualification history → FLAG

REPUTATION
──────────
□ Active media scandal (unresolved, ongoing negative coverage)
  Escalation: Systemic, unresolvable reputation damage → FLAG
□ Legal proceedings (material, unresolved, or likely to result in
  significant liability)
  Escalation: Litigation >20% of annual revenue → FLAG
□ Community opposition (for SEs: loss of social licence to operate)
  Escalation: Beneficiary community actively opposing the organisation → STOP

STOP = recommend halting the process until resolved
FLAG = raise with the decision-maker for explicit risk acceptance
════════════════════════════════════════════════════════════════
```

---

### 4.4 Risk Register

**What it is:** A living document cataloguing all identified risks with likelihood, impact, and mitigation status. Populated throughout the investigation and finalised in Phase 11.

**Template:**

```
RISK REGISTER — [Company]
══════════════════════════════════════════════════════════════════════════
ID  │ Risk               │ Category  │ L  │ I  │ Score │ Mitigation      │ Status
────┼────────────────────┼───────────┼────┼────┼───────┼─────────────────┼───────
R01 │ [risk description] │ [cat]     │ /5 │ /5 │ [LxI] │ [action]        │ [Open]
R02 │ [risk description] │ [cat]     │ /5 │ /5 │ [LxI] │ [action]        │ [Open]
══════════════════════════════════════════════════════════════════════════

Likelihood: 1=Rare, 2=Unlikely, 3=Possible, 4=Likely, 5=Almost Certain
Impact:     1=Negligible, 2=Minor, 3=Moderate, 4=Major, 5=Catastrophic
Score:      1-6=Low, 7-12=Medium, 13-19=High, 20-25=Critical

Categories: Financial, People, Market, Operational, Legal, Regulatory,
            Reputation, Technology, Governance, Mission (for SEs)

Status: Open / Mitigated / Accepted / Monitoring / Escalated

TOP 5 RISKS (by score):
1. [R##] — [risk] — Score: [n] — [one-line implication]
2. ...
```

---

### 4.5 RAG Dashboard

**What it is:** A one-page traffic-light summary across 10 assessment areas. This is always the FIRST PAGE of any synthesis output. See `references/synthesis-outputs.md` Section 1 for full rating criteria and weighting by investigation purpose.

**Template:**

```
RAG ASSESSMENT DASHBOARD — [Company]
═══════════════════════════════════════════════════════════════
Area                     │ Rating │ Key Finding
─────────────────────────┼────────┼───────────────────────────
Financial Health         │ R/A/G  │ [one-line justification]
Revenue Quality          │ R/A/G  │ [one-line justification]
Leadership & People      │ R/A/G  │ [one-line justification]
Customer Concentration   │ R/A/G  │ [one-line justification]
Market Position          │ R/A/G  │ [one-line justification]
Growth Trajectory        │ R/A/G  │ [one-line justification]
Governance & Compliance  │ R/A/G  │ [one-line justification]
Digital Maturity         │ R/A/G  │ [one-line justification]
Reputation               │ R/A/G  │ [one-line justification]
Strategic Alignment *    │ R/A/G  │ [one-line justification]
═══════════════════════════════════════════════════════════════
OVERALL: [R/A/G] — [one-sentence summary of the overall picture]

* Strategic Alignment = alignment with the user's stated purpose.
  A company can be financially healthy but strategically irrelevant.

Weighting: Areas most relevant to the investigation purpose carry
double weight in the overall assessment. See synthesis-outputs.md.
```

---

## 5. Social Enterprise Frameworks

### 5.1 Mission-Money Matrix

**What it is:** A 2x2 matrix plotting each of the organisation's activities on two axes: mission alignment and commercial return. Reveals whether the organisation is sustaining its mission through its commercial activities or cross-subsidising mission work with unrelated income.

**Template:**

```
MISSION-MONEY MATRIX — [Organisation]
════════════════════════════════════════════════════════════════

                     HIGH MISSION ALIGNMENT
                              │
    SWEET SPOT                │  MISSION-RICH,
    (high mission +           │  CASH-POOR
     high commercial)        │  (subsidised mission)
                              │
 HIGH COMMERCIAL ─────────────┼───────────── LOW COMMERCIAL
    RETURN                    │              RETURN
                              │
    CASH COW                  │  DANGER ZONE
    (low mission +            │  (low mission +
     high commercial)        │   low commercial)
                              │
                     LOW MISSION ALIGNMENT

Activities plotted:
──────────────────────────────────────────────────
Activity          │ Mission │ Commercial │ Quadrant    │ % Revenue
──────────────────┼─────────┼────────────┼─────────────┼──────────
[activity 1]      │ H/M/L   │ H/M/L      │ [quadrant]  │ [%]
[activity 2]      │ H/M/L   │ H/M/L      │ [quadrant]  │ [%]
════════════════════════════════════════════════════════════════

IMPLICATIONS:
- Sweet Spot activities: protect and grow these
- Mission-Rich/Cash-Poor: essential to mission but need subsidy — is that sustainable?
- Cash Cow: commercially strong but weak mission link — acceptable if subsidising
  mission work, but risk of mission drift if these grow too dominant
- Danger Zone: neither mission-aligned nor commercially viable — candidates for
  discontinuation
```

**So What? guidance:** A healthy social enterprise has the majority of revenue in the Sweet Spot quadrant. Heavy dependence on Cash Cow activities signals mission drift risk. If Danger Zone activities consume significant resources, the organisation is leaking value. For revenue discovery: identify which Mission-Rich/Cash-Poor activities could be moved toward the Sweet Spot through better pricing or market positioning.

---

### 5.2 Social Enterprise Typology

**What it is:** Classification of the social enterprise model to understand its structural dynamics, strengths, and vulnerabilities.

**Types:**

| Type | Description | Revenue Source | Strengths | Vulnerabilities |
|------|-------------|---------------|-----------|-----------------|
| **Employment Model** | Creates jobs for a target population (e.g. people with disability, refugees) | Sale of goods/services produced by the workforce | Direct mission delivery through operations | Productivity constraints, training costs, customer quality expectations |
| **Mission-Centric** | Products/services directly address a social need | Fees from beneficiaries, government contracts, NDIS | Revenue and mission fully aligned | Dependent on government policy/funding settings |
| **Cross-Subsidy** | Commercial arm funds separate social programs | Unrelated commercial revenue | Revenue not dependent on social mission buyers | Mission drift risk, complexity, internal competition for resources |
| **Cooperative** | Owned and governed by its members/beneficiaries | Member fees, sales to members/externally | Democratic governance, member loyalty | Slow decision-making, capital constraints |
| **Fee-for-Service** | Charges market rates for services with social outcomes | Client fees | Market-competitive, sustainable | Mission dilution if pricing excludes target population |
| **Environmental** | Addresses environmental issues through commercial activity | Product sales, carbon credits, waste diversion fees | Growing market demand | Commodity risk, certification costs, greenwashing scrutiny |

**Template:**

```
SOCIAL ENTERPRISE TYPOLOGY — [Organisation]
════════════════════════════════════════════════════════════════
Primary type:     [type]
Secondary type:   [type, if hybrid]
Classification confidence: [High/Medium/Low]

Type-specific assessment:
- Revenue alignment with mission: [Strong/Moderate/Weak]
- Structural vulnerability:       [key risk for this type]
- Growth pathway:                 [what scaling looks like for this type]
- Comparable peers:               [3-5 similar organisations]
```

---

### 5.3 Theory of Change Analysis

**What it is:** Assessment of the logical coherence of the organisation's impact model — the chain from resources deployed to ultimate social impact.

**Template:**

```
THEORY OF CHANGE — [Organisation]
════════════════════════════════════════════════════════════════

INPUTS              →  ACTIVITIES          →  OUTPUTS
[what they invest]     [what they do]         [what they produce]
- $[budget]            - [activity 1]         - [output 1, with #]
- [staff/volunteers]   - [activity 2]         - [output 2, with #]
- [partners]           - [activity 3]         - [output 3, with #]
- [infrastructure]

OUTCOMES            →  IMPACT
[changes in people/    [long-term systemic
 communities]           change]
- [outcome 1]          - [impact claim]
- [outcome 2]
- [outcome 3]

COHERENCE ASSESSMENT:
─────────────────────
Link                  │ Strength │ Evidence │ Assumptions
──────────────────────┼──────────┼──────────┼──────────────
Inputs → Activities   │ S/M/W    │ [source] │ [assumptions]
Activities → Outputs  │ S/M/W    │ [source] │ [assumptions]
Outputs → Outcomes    │ S/M/W    │ [source] │ [assumptions]
Outcomes → Impact     │ S/M/W    │ [source] │ [assumptions]

GAPS AND WEAKNESSES:
- [where the logic chain breaks or depends on untested assumptions]
- [outcomes claimed without evidence]
- [activities that do not logically connect to stated impact]
```

**So What? guidance:** A weak link in the chain means the impact claim is aspirational rather than evidenced. This matters for: funders (are they funding actual impact?), partners (will this partnership deliver the promised social return?), boards (is the organisation doing what it says it does?). Organisations with strong inputs-to-outputs links but weak outcomes-to-impact links are common — they are measuring activity, not change.

---

### 5.4 Mission Drift Diagnostic

**What it is:** An 8-indicator assessment of whether a social enterprise is drifting away from its stated mission. Mission drift is gradual, often invisible to those inside the organisation, and is one of the most common failure modes for social enterprises.

**Template:**

```
MISSION DRIFT DIAGNOSTIC — [Organisation]
════════════════════════════════════════════════════════════════
Indicator                    │ Signal │ Evidence              │ Score
─────────────────────────────┼────────┼───────────────────────┼──────
1. Revenue Source Shift       │ R/A/G  │ [earned vs grant vs   │ /10
   (increasing % from non-   │        │  fee-for-service mix  │
    mission-aligned sources)  │        │  over time]           │
                              │        │                       │
2. Language Change            │ R/A/G  │ [compare mission      │ /10
   (mission language fading   │        │  language: website    │
    from external comms)      │        │  now vs 2-3 yrs ago] │
                              │        │                       │
3. Beneficiary Profile Change │ R/A/G  │ [serving different    │ /10
   (serving easier/wealthier  │        │  population than      │
    populations over time)    │        │  originally intended] │
                              │        │                       │
4. Board Composition Shift    │ R/A/G  │ [commercial expertise │ /10
   (mission expertise being   │        │  replacing lived exp. │
    replaced by commercial)   │        │  or sector expertise] │
                              │        │                       │
5. Strategy Pivot             │ R/A/G  │ [strategic plan       │ /10
   (strategy emphasising      │        │  priorities shifting  │
    growth/revenue over       │        │  from impact to       │
    impact)                   │        │  commercial metrics]  │
                              │        │                       │
6. Hiring Pattern Change      │ R/A/G  │ [new hires from       │ /10
   (recruiting from corporate │        │  corporate vs social  │
    rather than social sector)│        │  sector backgrounds]  │
                              │        │                       │
7. Partnership Selection      │ R/A/G  │ [partnering for $     │ /10
   (partnerships chosen for   │        │  rather than mission  │
    revenue rather than       │        │  alignment]           │
    mission alignment)        │        │                       │
                              │        │                       │
8. Geographic Expansion       │ R/A/G  │ [expanding to         │ /10
   (expanding to lucrative    │        │  commercially         │
    markets rather than areas │        │  attractive markets   │
    of greatest need)         │        │  vs areas of need]    │
════════════════════════════════════════════════════════════════
Composite Score: [x]/80
Drift Rating: None (70-80) / Early (50-69) / Moderate (30-49) / Severe (<30)

Note: Mission drift is not inherently negative if conscious and strategic.
The issue is UNCONSCIOUS drift, where the organisation no longer recognises
it has moved away from its original mission.
```

**So What? guidance:** Moderate or Severe drift rating should be raised directly with the user. For partnerships: are you partnering with the organisation they are today or the one they were? For funders: is your money going where you think it is? For boards: this diagnostic is a governance tool. For revenue discovery: sometimes mission drift is rational — the market is telling the organisation where it can be sustainable.

---

### 5.5 Three-Market Model

**What it is:** Social enterprises operate in three distinct markets simultaneously, unlike conventional businesses which primarily serve one. The health of all three markets determines organisational sustainability. Weakness in any one market will eventually undermine the other two.

**Template:**

```
THREE-MARKET MODEL — [Organisation]
════════════════════════════════════════════════════════════════

IMPACT MARKET (beneficiaries and their communities)
───────────────────────────────────────────────────
Beneficiary population:     [who, how many, where]
Access and reach:           [% of target population reached]
Beneficiary satisfaction:   [evidence — surveys, retention, feedback]
Outcomes evidence:          [what measurable change is achieved]
Community perception:       [how the community views the organisation]
Social licence strength:    [Strong / Moderate / Fragile]
Health:                     [R/A/G]

REVENUE MARKET (paying customers, procurement, funders)
──────────────────────────────────────────────────────
Customer segments:          [who pays, and for what]
Revenue diversity:          [see Revenue Decomposition framework]
Market competitiveness:     [position vs commercial competitors]
Funder relationships:       [depth, duration, renewal rates]
Procurement positioning:    [social procurement certifications, panel status]
Pipeline visibility:        [forward revenue visibility in months]
Health:                     [R/A/G]

TALENT MARKET (staff, volunteers, board)
────────────────────────────────────────
Staff headcount and trend:  [number, growth/decline]
Volunteer base:             [number, engagement level]
Board composition:          [skills, diversity, lived experience]
Staff turnover rate:        [% annually, benchmark comparison]
Employer brand strength:    [Glassdoor, reputation in sector]
Recruitment difficulty:     [ease of filling roles]
Cultural coherence:         [mission alignment across team]
Health:                     [R/A/G]

CROSS-MARKET DYNAMICS:
- Impact ↔ Revenue:  [Does impact performance drive revenue? e.g. outcome-based contracts]
- Impact ↔ Talent:   [Does mission attract and retain talent? Or burn them out?]
- Revenue ↔ Talent:  [Can revenue support competitive compensation? Retention risk?]

OVERALL THREE-MARKET HEALTH: [R/A/G]
Weakest market:             [which one, and why it matters]
```

**So What? guidance:** The weakest market determines the organisation's ceiling. A social enterprise with strong impact and talent but weak revenue will eventually burn through reserves and lose both. Strong revenue but deteriorating impact will lose social licence, and eventually talent. For partnerships and investment: assess whether your engagement strengthens the weakest market or just the strongest.

---

### 5.6 SROI Estimation (Simplified)

**What it is:** A simplified Social Return on Investment estimation for when full SROI data is not available. Uses proxies and benchmarks rather than primary research.

**Template:**

```
SROI ESTIMATION (SIMPLIFIED) — [Organisation]
════════════════════════════════════════════════════════════════
Investment (annual):         $[total cost of delivering social programs]

Outcome                 │ Beneficiaries │ Proxy Value │ Total Value │ Source
────────────────────────┼───────────────┼─────────────┼─────────────┼───────
[outcome 1: e.g.        │ [number]      │ $[per person]│ $[total]   │ [proxy
 employment gained]     │               │              │            │  source]
[outcome 2: e.g.        │ [number]      │ $[per person]│ $[total]   │ [proxy
 housing stabilised]    │               │              │            │  source]
────────────────────────┼───────────────┼─────────────┼─────────────┼───────
Total Social Value:     │               │              │ $[sum]     │

SROI Ratio:             [total social value] : [investment] = [x]:1

Confidence:             [Low — estimation only. Not a certified SROI.]
Key assumptions:        [list the proxy values used and their sources]
Sensitivity:            [if the largest outcome is halved, SROI = [x]:1]

Note: This is an indicative estimation, not a certified SROI assessment.
Proxy values should be drawn from published government valuations
(e.g. cost of unemployment, cost of homelessness, cost of incarceration)
where available.
```

**So What? guidance:** Even a rough SROI estimate provides a powerful communication tool. If the ratio is clearly above 2:1 on conservative estimates, the organisation is generating meaningful social value. Below 1:1, the organisation may be destroying value — spending more than the social return it generates. Use the sensitivity analysis to test whether the ratio holds under less optimistic assumptions.

---

### 5.7 Revenue Discovery Framework

**What it is:** A structured approach for identifying revenue opportunities for social enterprises in financial crisis. Used in Revenue Discovery mode (Phase 10b) and whenever a social enterprise target shows financial distress signals.

**Template:**

```
REVENUE DISCOVERY — [Organisation]
════════════════════════════════════════════════════════════════

STEP 1: CURRENT CAPABILITIES AUDIT
───────────────────────────────────
Capability            │ Utilisation │ Market Demand │ Margin │ Scale?
──────────────────────┼────────────┼───────────────┼────────┼───────
[capability 1]        │ [% used]   │ H/M/L         │ H/M/L  │ Y/N
[capability 2]        │ [% used]   │ H/M/L         │ H/M/L  │ Y/N
[capability 3]        │ [% used]   │ H/M/L         │ H/M/L  │ Y/N

Unused capacity:      [assets, skills, time, space not fully utilised]
Hidden assets:        [brand, relationships, data, IP, certifications]

STEP 2: ADJACENT SERVICES
─────────────────────────
Adjacent Service      │ Gap to Deliver │ Market Size │ Mission Fit
──────────────────────┼────────────────┼─────────────┼────────────
[service 1]           │ [what's needed]│ [est. $]    │ H/M/L
[service 2]           │ [what's needed]│ [est. $]    │ H/M/L

STEP 3: MARKET DEMAND MATCHING
──────────────────────────────
Demand Source                │ Opportunity               │ Match Score
────────────────────────────┼───────────────────────────┼───────────
Social procurement (govt)    │ [specific tenders/panels] │ /10
Corporate ESG/RAP spending   │ [specific companies]      │ /10
NDIS/aged care/health        │ [specific service gaps]   │ /10
Infrastructure projects      │ [specific projects]       │ /10
Philanthropic/grant pipeline │ [specific programs]       │ /10

STEP 4: QUICK WIN IDENTIFICATION
────────────────────────────────
Timeframe     │ Opportunity           │ Revenue Est. │ Effort │ Risk
──────────────┼───────────────────────┼──────────────┼────────┼─────
0-90 days     │ [quick wins]          │ $[amount]    │ L/M/H  │ L/M/H
6-12 months   │ [medium-term builds]  │ $[amount]    │ L/M/H  │ L/M/H
12+ months    │ [strategic pivots]    │ $[amount]    │ L/M/H  │ L/M/H

PRIORITISED ACTION PLAN:
1. [highest priority action — quick, high-return, low-risk]
2. [second priority]
3. [third priority]
```

---

## 6. Sales and Engagement Frameworks

### 6.1 MEDDPICC Pre-Meeting Scorecard

**What it is:** A qualification framework for complex B2B sales. Before engaging with the target, score what is known and what needs discovery across eight dimensions. This focuses meeting preparation and ensures no critical dimension is ignored.

**Template:**

```
MEDDPICC PRE-MEETING SCORECARD — [Target Company]
════════════════════════════════════════════════════════════════
Dimension         │ Known                │ Gap / To Discover    │ Score
──────────────────┼──────────────────────┼──────────────────────┼──────
Metrics           │ [what success looks  │ [what we don't know  │ /10
(how they measure │  like for them —     │  about their KPIs,   │
 success)         │  KPIs, targets]      │  targets, pain $]    │

Economic Buyer    │ [who controls the    │ [access level,       │ /10
(who signs off)   │  budget — name/role] │  priorities unknown] │

Decision Criteria │ [what they evaluate  │ [weighting,          │ /10
(how they choose) │  — price, quality,   │  hidden criteria]    │
                  │  social impact, etc] │                      │

Decision Process  │ [how they decide —   │ [steps, timeline,    │ /10
(steps and timing)│  committee, tender,  │  approval chain]     │
                  │  board approval]     │                      │

Paper Process     │ [how contracts get   │ [procurement rules,  │ /10
(procurement)     │  done — procurement, │  legal review,       │
                  │  legal, compliance]  │  insurance reqs]     │

Identify Pain     │ [their problems —    │ [pain severity,      │ /10
(why they'd act)  │  from job posts,     │  urgency, cost of    │
                  │  media, reviews]     │  inaction]           │

Champion          │ [internal advocate   │ [do we have one?     │ /10
(inside ally)     │  — who, access,      │  how to find one?]   │
                  │  motivation]         │                      │

Competition       │ [who else is in the  │ [incumbent,          │ /10
(alternatives)    │  frame — direct and  │  their weaknesses,   │
                  │  indirect]           │  switching cost]     │
════════════════════════════════════════════════════════════════
Composite Score:  [x]/80
Readiness:        Ready (60+) / Needs Work (40-59) / Not Ready (<40)

TOP 3 DISCOVERY PRIORITIES FOR FIRST MEETING:
1. [most critical gap to fill]
2. [second most critical]
3. [third most critical]
```

---

### 6.2 Decision-Making Unit (DMU) Mapping

**What it is:** Maps every person involved in the buying decision, their role, their priorities, and the engagement strategy for each.

**Template:**

```
DECISION-MAKING UNIT — [Target Company]
════════════════════════════════════════════════════════════════
Role            │ Name        │ Title        │ Priorities       │ Access │ Strategy
────────────────┼─────────────┼──────────────┼──────────────────┼────────┼─────────
Economic Buyer  │ [name]      │ [title]      │ [ROI, budget,    │ H/M/L  │ [approach]
(approves $)    │             │              │  risk reduction] │        │

Technical Buyer │ [name]      │ [title]      │ [specs, quality, │ H/M/L  │ [approach]
(evaluates fit) │             │              │  compliance]     │        │

User Buyer      │ [name]      │ [title]      │ [usability,      │ H/M/L  │ [approach]
(will use it)   │             │              │  daily impact]   │        │

Champion        │ [name]      │ [title]      │ [career win,     │ H/M/L  │ [approach]
(advocates)     │             │              │  problem solved] │        │

Blocker         │ [name]      │ [title]      │ [incumbent       │ H/M/L  │ [approach]
(resists)       │             │              │  protection,     │        │
                │             │              │  change averse]  │        │

Influencer      │ [name]      │ [title]      │ [reputation,     │ H/M/L  │ [approach]
(shapes opinion)│             │              │  industry views] │        │
════════════════════════════════════════════════════════════════

POWER MAP:
- Strongest influence on decision:  [name — why]
- Weakest link / vulnerability:     [name — why]
- Unidentified roles:               [which DMU roles have no name yet]
- Engagement sequence:              [who to contact first, second, etc.]
```

**So What? guidance:** Never engage a target without knowing the Economic Buyer and having a path to the Champion. If the Blocker has more power than the Champion, re-evaluate the approach. Unidentified roles are gaps that should drive the first meeting's discovery agenda.

---

### 6.3 Power-Interest Grid

**What it is:** A 2x2 stakeholder prioritisation matrix plotting each stakeholder on power (ability to affect the outcome) vs interest (motivation to engage).

**Template:**

```
POWER-INTEREST GRID — [Target Company / Decision]
════════════════════════════════════════════════════════════════

                          HIGH INTEREST
                              │
    MANAGE CLOSELY            │  KEEP INFORMED
    (high power +             │  (low power +
     high interest)           │   high interest)
    → Key players             │  → Supporters/advocates
    → Engage deeply           │  → Communicate regularly
                              │
 HIGH POWER ──────────────────┼────────────────── LOW POWER
                              │
    KEEP SATISFIED            │  MONITOR
    (high power +             │  (low power +
     low interest)            │   low interest)
    → Potential blockers      │  → Minimal effort
    → Don't surprise them     │  → Watch for changes
                              │
                          LOW INTEREST

Stakeholders plotted:
───────────────────────────────────────────────────
Name / Role         │ Power │ Interest │ Quadrant         │ Action
────────────────────┼───────┼──────────┼──────────────────┼──────────
[stakeholder 1]     │ H/M/L │ H/M/L    │ [quadrant]       │ [action]
[stakeholder 2]     │ H/M/L │ H/M/L    │ [quadrant]       │ [action]
```

---

### 6.4 Buying Signal Register

**What it is:** A log of observed signals that indicate the target may be ready, willing, or forced to buy. Signals are categorised by type and assessed for confidence and timing.

**Template:**

```
BUYING SIGNAL REGISTER — [Target Company]
════════════════════════════════════════════════════════════════
Signal Type    │ Signal              │ Source    │ Date   │ Conf. │ Implication
───────────────┼─────────────────────┼──────────┼────────┼───────┼───────────
Growth         │ [new office, hiring │ [source] │ [date] │ H/M/L │ [what it
               │  spree, fundraise]  │          │        │       │  means]
Leadership     │ [new CEO, new CTO,  │ [source] │ [date] │ H/M/L │ [what it
Change         │  board refresh]     │          │        │       │  means]
Funding Event  │ [investment round,  │ [source] │ [date] │ H/M/L │ [what it
               │  grant received]    │          │        │       │  means]
Strategic      │ [partnership, pivot,│ [source] │ [date] │ H/M/L │ [what it
Initiative     │  new market entry]  │          │        │       │  means]
Pain Signal    │ [negative reviews,  │ [source] │ [date] │ H/M/L │ [what it
               │  complaints, media] │          │        │       │  means]
Contract       │ [known expiry,      │ [source] │ [date] │ H/M/L │ [what it
Expiry         │  tender announced]  │          │        │       │  means]
════════════════════════════════════════════════════════════════

SIGNAL STRENGTH SUMMARY:
- Total signals identified:    [n]
- Strong buying window now:    [Yes/No — reasoning]
- Optimal approach timing:     [recommendation]
- Recommended trigger event:   [what to wait for, if timing is not right]
```

---

### 6.5 Pain Point Register

**What it is:** A compilation of pain points extracted from multiple sources, mapped to potential offerings. Pain points are more reliable than stated needs because they are often expressed involuntarily.

**Template:**

```
PAIN POINT REGISTER — [Target Company]
════════════════════════════════════════════════════════════════
Pain Point          │ Source(s)        │ Severity │ Frequency │ Our Solution?
────────────────────┼──────────────────┼──────────┼───────────┼──────────────
[pain point 1]      │ [Glassdoor,      │ H/M/L    │ [how often│ [Y/N —
                    │  job posts, etc] │          │  mentioned]│  which offer]
[pain point 2]      │ [media, reviews, │ H/M/L    │ [how often│ [Y/N —
                    │  website gaps]   │          │  mentioned]│  which offer]
════════════════════════════════════════════════════════════════

Source types: Job postings (skills they can't find), Glassdoor reviews
(internal dysfunction), Media coverage (public problems), Website messaging
(problems they claim to solve for others — often projections of own pain),
Customer reviews (service failures), Social media (complaints),
Industry reports (sector-wide challenges)

TOP 3 PAIN POINTS FOR ENGAGEMENT:
1. [most acute, most aligned with our offering]
2. [second]
3. [third]

PAIN-TO-PITCH MAP:
[For each of the top 3, draft the opening question or statement that
 connects their pain to your capability without making a sales pitch]
```

---

## 7. Scenario Analysis

### 7.1 Three-Scenario Framework (Bull / Base / Bear)

**What it is:** Three plausible futures for the target, used to bound the range of outcomes and identify key uncertainties. Avoids the trap of single-point forecasting.

**Template:**

```
SCENARIO ANALYSIS — [Company]
════════════════════════════════════════════════════════════════

               │ BULL (Upside)    │ BASE (Most Likely) │ BEAR (Downside)
───────────────┼──────────────────┼────────────────────┼─────────────────
Probability    │ [%]              │ [%]                │ [%]
───────────────┼──────────────────┼────────────────────┼─────────────────
Key Assumptions│ [what must be    │ [continuation of   │ [what goes
               │  true for this   │  current trends    │  wrong for this
               │  scenario]       │  with known risks] │  scenario]
───────────────┼──────────────────┼────────────────────┼─────────────────
Revenue        │ $[amount]        │ $[amount]          │ $[amount]
(12-month fwd) │                  │                    │
───────────────┼──────────────────┼────────────────────┼─────────────────
Key Drivers    │ [what propels    │ [what sustains     │ [what causes
               │  the upside]     │  the baseline]     │  the decline]
───────────────┼──────────────────┼────────────────────┼─────────────────
Implications   │ [what this means │ [what this means   │ [what this means
for User       │  for the user's  │  for the user's    │  for the user's
               │  decision]       │  decision]         │  decision]
═══════════════════════════════════════════════════════════════

TRIGGER EVENTS (what would shift from Base to Bull or Bear):
- To Bull: [specific events — new contract, market shift, hire]
- To Bear: [specific events — customer loss, regulation, key person exit]

KEY UNCERTAINTIES (factors that most affect which scenario materialises):
1. [uncertainty 1]
2. [uncertainty 2]
3. [uncertainty 3]
```

**So What? guidance:** The value is in the implications row and the trigger events. The user does not need to know the exact probability — they need to know what to watch for and how to respond. If the BEAR scenario is catastrophic and the triggers are plausible, that dominates the decision regardless of probability.

---

### 7.2 Early Warning Indicators

**What it is:** A monitoring plan tied to each scenario, specifying what signals would indicate a scenario is becoming reality. Designed to be acted on — not just observed.

**Template:**

```
EARLY WARNING INDICATORS — [Company]
════════════════════════════════════════════════════════════════
Scenario │ Indicator              │ Source          │ Frequency │ Action if Triggered
─────────┼────────────────────────┼─────────────────┼───────────┼────────────────────
BULL     │ [signal of upside]     │ [where to check]│ [cadence] │ [what to do]
BULL     │ [signal of upside]     │ [where to check]│ [cadence] │ [what to do]
BASE     │ [signal of stability]  │ [where to check]│ [cadence] │ [continue monitoring]
BEAR     │ [signal of downside]   │ [where to check]│ [cadence] │ [escalate / act]
BEAR     │ [signal of downside]   │ [where to check]│ [cadence] │ [escalate / act]
════════════════════════════════════════════════════════════════

MONITORING PLAN:
- Google Alerts configured for: [search terms]
- Regulatory filings to check: [which registers, when filed]
- Financial reporting dates: [when next accounts due]
- Key contract/event dates: [known milestones]
- Refresh cadence: [recommended interval for full refresh]
```

---

## 8. Capability Assessment

### 8.1 Capability vs Capacity Matrix

**What it is:** Distinguishes what the target CAN do (capability) from what they ARE doing (utilisation). The gap between the two represents either untapped potential or strategic under-investment.

**Template:**

```
CAPABILITY vs CAPACITY — [Company]
════════════════════════════════════════════════════════════════
Capability         │ Evidence of   │ Current       │ Gap       │ Reason for
                   │ Capability    │ Utilisation   │           │ Gap
───────────────────┼───────────────┼───────────────┼───────────┼──────────────
[capability 1]     │ [how we know  │ [what they're │ [under/   │ [choice,
                   │  they can]    │  actually doing]│ over/fit]│  constraint,
                   │               │                │          │  ignorance]
[capability 2]     │ [evidence]    │ [utilisation]  │ [gap]    │ [reason]
════════════════════════════════════════════════════════════════

UNDER-UTILISED CAPABILITIES (opportunity):
- [capability with low utilisation and high market demand]

OVER-STRETCHED CAPABILITIES (risk):
- [capability operating beyond sustainable capacity]

MISSING CAPABILITIES (gap):
- [capability required by market/strategy but not present]
```

---

### 8.2 Technology Maturity Assessment

**What it is:** Assessment of the target's technology infrastructure, tools, and digital capability. Informs integration risk, scalability, and operational efficiency.

**Template:**

```
TECHNOLOGY MATURITY — [Company]
════════════════════════════════════════════════════════════════
Area                  │ Current State │ Maturity │ Evidence │ Risk
──────────────────────┼──────────────┼──────────┼──────────┼──────
Core Infrastructure   │ [cloud/on-   │ 1-5      │ [source] │ H/M/L
(hosting, servers)    │  prem/hybrid]│          │          │

Business Applications │ [CRM, ERP,   │ 1-5      │ [source] │ H/M/L
(operational systems) │  finance, HR]│          │          │

Digital Presence      │ [website,    │ 1-5      │ [source] │ H/M/L
(web, mobile, social) │  quality,    │          │          │
                      │  mobile-     │          │          │
                      │  responsive] │          │          │

Data & Analytics      │ [reporting,  │ 1-5      │ [source] │ H/M/L
(insight capability)  │  dashboards, │          │          │
                      │  data-driven]│          │          │

Cybersecurity         │ [evident     │ 1-5      │ [source] │ H/M/L
(protection posture)  │  measures,   │          │          │
                      │  compliance] │          │          │

Integration           │ [API-ready,  │ 1-5      │ [source] │ H/M/L
(connectedness)       │  manual,     │          │          │
                      │  siloed]     │          │          │
════════════════════════════════════════════════════════════════
Maturity Scale: 1=Ad hoc, 2=Basic, 3=Defined, 4=Managed, 5=Optimised
Overall Maturity: [average score and assessment]
```

---

### 8.3 Organisational Readiness Assessment

**What it is:** Evaluates whether the target is ready for a specific engagement — partnership, acquisition, scaling, or transformation.

**Template:**

```
ORGANISATIONAL READINESS — [Company] — [Ready for what?]
════════════════════════════════════════════════════════════════
Dimension             │ Assessment │ Evidence             │ Rating
──────────────────────┼────────────┼──────────────────────┼───────
Leadership Alignment  │ [unified   │ [board minutes,      │ R/A/G
                      │  vision?]  │  media, strategy]    │
Financial Capacity    │ [can they  │ [cash position,      │ R/A/G
                      │  afford it]│  debt capacity]      │
Operational Maturity  │ [systems   │ [processes,          │ R/A/G
                      │  in place?]│  documentation]      │
Cultural Fit          │ [values    │ [Glassdoor, mission, │ R/A/G
                      │  match?]   │  working style]      │
Change Capacity       │ [bandwidth │ [current initiatives,│ R/A/G
                      │  for this?]│  team stability]     │
Governance            │ [decision- │ [board structure,    │ R/A/G
                      │  making    │  delegation,         │
                      │  effective]│  compliance]         │
════════════════════════════════════════════════════════════════
Overall Readiness: [Ready / Ready with conditions / Not ready]
Conditions: [what would need to change before proceeding]
```

---

## 9. Forward-Looking Analysis

### 9.1 Strategic Options Assessment

**What it is:** Maps the target's strategic options based on their current position, capabilities, and market dynamics. Used to anticipate their next moves and assess alignment with the user's interests.

**Template:**

```
STRATEGIC OPTIONS — [Company]
════════════════════════════════════════════════════════════════
Option              │ Feasibility │ Attractiveness │ Likelihood │ User Impact
────────────────────┼─────────────┼────────────────┼────────────┼────────────
GROWTH OPTIONS
[organic growth]    │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]
[acquisition]       │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]
[new market entry]  │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]
[new product dev]   │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]

RISK MITIGATION
[diversification]   │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]
[cost reduction]    │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]
[partnership]       │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]

EXIT / TRANSITION
[sale / IPO]        │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]
[merger]            │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]
[wind-down]         │ H/M/L       │ H/M/L          │ H/M/L      │ [+ / - / ~]
════════════════════════════════════════════════════════════════

Most likely strategic direction:  [assessment with evidence]
Implication for user:            [how this affects the user's decision/approach]
```

---

### 9.2 Valuation Indicators

**What it is:** Indicative valuation range using multiple approaches. These are indicators for context — not formal valuations. Clearly flag this distinction.

**Template:**

```
VALUATION INDICATORS — [Company]
════════════════════════════════════════════════════════════════
⚠ THESE ARE INDICATIVE ONLY — NOT A FORMAL VALUATION ⚠

Method                    │ Basis          │ Multiple/Rate │ Indicative Value
──────────────────────────┼────────────────┼───────────────┼─────────────────
Revenue Multiple          │ $[revenue]     │ [x]x          │ $[range]
  (comparable companies)  │                │               │
EBITDA Multiple           │ $[EBITDA]      │ [x]x          │ $[range]
  (comparable companies)  │                │               │
Revenue Run-Rate          │ $[monthly ×12] │ [x]x          │ $[range]
  (if early-stage)        │                │               │
Asset-Based Floor         │ $[net assets]  │               │ $[amount]
  (liquidation value)     │                │               │
DCF Indicative            │ $[FCF]         │ [WACC %]      │ $[range]
  (if sufficient data)    │                │ [growth %]    │
════════════════════════════════════════════════════════════════

Comparable companies used:  [list with their multiples and sources]

Premium/Discount factors:
  + [strategic value, IP, market position — justify premium]
  - [key person risk, customer concentration — justify discount]
  - [illiquidity discount for private company]

Indicative range:  $[low] — $[high]
Central estimate:  $[mid]  (confidence: [Low/Medium])
```

**So What? guidance:** This is not a valuation — state this clearly. It provides a frame of reference for whether a price is in the right ballpark. Revenue multiples vary enormously by industry, growth rate, and quality of revenue (see Revenue Sustainability Scorecard). The discount factors are often more important than the base multiple.

---

### 9.3 Integration / Partnership Risk Assessment

**What it is:** Assessment of risks specific to combining or closely aligning with the target organisation.

**Template:**

```
INTEGRATION / PARTNERSHIP RISK — [Company]
════════════════════════════════════════════════════════════════
Risk Area             │ Assessment │ Severity │ Mitigation
──────────────────────┼────────────┼──────────┼─────────────────
Cultural Compatibility│ [values,   │ H/M/L    │ [how to manage]
                      │  work style│          │
                      │  alignment]│          │
System Complexity     │ [tech stack│ H/M/L    │ [integration
                      │  overlap,  │          │  approach]
                      │  migration]│          │
Contract Portability  │ [can client│ H/M/L    │ [change of
                      │  contracts │          │  control clauses,
                      │  transfer?]│          │  consent needed]
Key Person Retention  │ [will key  │ H/M/L    │ [retention
                      │  people    │          │  mechanisms —
                      │  stay?]    │          │  earnout, equity]
Regulatory Approval   │ [ACCC,     │ H/M/L    │ [timeline,
                      │  FIRB, or  │          │  conditions]
                      │  industry- │          │
                      │  specific] │          │
Brand / Reputation    │ [will the  │ H/M/L    │ [brand strategy,
                      │  associa-  │          │  communication]
                      │  tion help │          │
                      │  or harm?] │          │
Operational Overlap   │ [redundan- │ H/M/L    │ [rationalisation
                      │  cies, team│          │  plan]
                      │  duplica-  │          │
                      │  tion]     │          │
════════════════════════════════════════════════════════════════
Overall Integration Risk: [High / Medium / Low]
Top 3 risks to address before proceeding:
1. [risk — action]
2. [risk — action]
3. [risk — action]
```

**So What? guidance:** The most commonly underestimated integration risks are cultural compatibility and key person retention. Systems can be migrated. Contracts can be renegotiated. But if the key people leave or the cultures clash, the value being acquired evaporates. For partnerships (as distinct from acquisitions), contract portability and brand/reputation risk tend to dominate.

---

## Narrative Consistency Audit

**What it is:** A structured check that the story told by one source coheres with what other independent sources say about the same entity. Unlike Triangulation (which checks specific claims), the Narrative Consistency Audit checks whether the *overall picture* holds together.

**When to use:** During Phase 11 synthesis, after the Triangulation Matrix is built.

**The audit:**

1. **State the central narrative** in one paragraph — the story that emerges from the research as a whole
2. **List the three strongest pieces of evidence** supporting it
3. **List the three pieces of evidence that most cut against it** (or are ambiguous)
4. **Identify any anomalies** — facts that don't fit neatly into either column
5. **Verdict:** Is the central narrative robust, qualified, or contested?

```
NARRATIVE CONSISTENCY AUDIT — [Subject]
══════════════════════════════════════════════════════
Central narrative:
[1-2 sentence summary of the overall picture]

Supporting evidence:
  1. [strongest supporting fact + source]
  2. [second supporting fact + source]
  3. [third supporting fact + source]

Counter-evidence:
  1. [most significant counter-fact + source]
  2. [second counter-fact + source]
  3. [third counter-fact + source]

Anomalies: [facts that don't fit the narrative and can't yet be explained]

Verdict: [Robust / Qualified / Contested]
Rationale: [1-2 sentences explaining the verdict]
══════════════════════════════════════════════════════
```

**Relationship to Triangulation:** Triangulation checks claims one at a time. The Narrative Consistency Audit checks whether the claims, taken together, tell a coherent story. Both are needed for Full Investigation tier.

**So What? guidance:** A "Contested" verdict does not mean the investigation has failed — it means the subject is genuinely complex and the reader needs to know that. Never suppress a Contested verdict to make the synthesis look cleaner.

---

## Framework Selection Guide

Use this quick reference to select frameworks based on investigation purpose:

| Purpose | Always Apply | Purpose-Specific |
|---------|-------------|------------------|
| **All investigations** | SWOT, RAG Dashboard, Timeline, Risk Register | — |
| **Competitive analysis** | Porter's Five Forces, Value Chain | Capability vs Capacity, Strategic Options |
| **Sales / BD** | MEDDPICC, DMU Mapping, Power-Interest Grid | Buying Signals, Pain Points, PESTLE |
| **Due diligence** | Revenue Decomposition, Working Capital, Normalised Earnings | Deal-Breaker Checklist, KPD Matrix, Customer Concentration, Valuation Indicators |
| **Partnership** | Organisational Readiness, Integration Risk | 7S Framework, Business Model Canvas |
| **Social enterprise** | Three-Market Model, Mission Drift, Typology | Theory of Change, Mission-Money Matrix, SROI, Revenue Discovery |
| **Investment** | Revenue Sustainability Scorecard, Unit Economics, Scenario Analysis | Common-Size Financials, Early Warning Indicators |
| **Integrity investigation** | ACH, KAC, Deal-Breaker Checklist | Timeline (pattern detection), KPD Matrix |

Every framework output in the final synthesis MUST include a "So What?" paragraph connecting the analysis to the user's stated purpose from Phase 0.
