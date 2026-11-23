# Investigation Setup

Read this file at the start of every investigation. It holds the dependency check, the disambiguation rules, the invocation menus, the investigation tiers, the web access layers, and the dossier folder structure.

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

---

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
