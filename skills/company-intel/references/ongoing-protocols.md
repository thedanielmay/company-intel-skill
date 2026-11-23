# Ongoing Protocols

Read this file during and after the research waves. It holds progress reporting, the research log format, confidence ratings, source saturation, and the refresh protocol.

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
