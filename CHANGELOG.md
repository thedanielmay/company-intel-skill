# Changelog

## 1.6.0 - 2026-11-23

- Narrowed the description so the skill starts on a request for research, due diligence, a dossier, a deep dive, a brief or intelligence on a named subject, or when the user names the skill. Removed the phrases that started the skill on any mention of a company. Kept the note that sends industry, market, sector, policy and regulation subjects to topic-intel.
- Removed the default from Full Investigation. The skill asks the user to choose a depth. Quick Scan is the suggested depth. Use a depth named in the request without asking again.
- Removed the setup block duplicated between SKILL.md and references/investigation-setup.md. SKILL.md now points to that reference for the dependency check, disambiguation, invocation modes, depth menu, web access and folder structure.
- Added a one-line load trigger to each reference in the SKILL.md list that lacked a phase or step.

## 1.5.0 - 2026-11-23

- Added sanctions and PEP screening of the company, directors and beneficial owners against the DFAT, OFAC, UN, UK and EU lists and against PEP data. Each check records its date. A name match is a possible match until identity matching confirms it. A clear result reads "no match found on <date>", not "clean".
- Added an identity matching rule for director and person searches. Two records link only when two independent identifiers agree. A name alone never links them. Unconfirmed matches are reported as separate people.
- Added a cost note for ASIC company and person extracts and other paid register extracts. The skill asks the user before buying an extract and names the register and price shown.
- Moved director and beneficial owner property and home address searches behind the Phase 0 privacy checkpoint. They run only when the user confirms a due diligence purpose that needs them.
- Claims now use the two grades in INTELLIGENCE-STANDARDS.md Section 4. The grades are source reliability A to F and information credibility 1 to 6. Write them together, for example B2. Added a funder check for analyst, industry, think-tank and vendor reports. A report funded by an interested party cannot grade above C for reliability on that topic. Keep ⚠ for a claim another source contradicts. Scenario likelihood uses words instead of percentages. Use remote, unlikely, roughly even, likely or almost certain.

## 1.4.0 - 2026-11-23

- Made Layer 4 (Playwright) opt in per source. The skill names the source and the reason before each ask, and logs a gap on a no or a missing install.
- Removed the headed login capture and headless cookie reuse template. A source behind a login is a gap unless the user reads it and pastes what they want used.
- Removed stealth, user-agent spoofing and the stealth installation check. Playwright now runs as a normal browser that identifies as automation.
- Removed LinkedIn from Layer 4 target lists. Phase 4 uses only public content from Layers 1 to 3 or content the user pastes.
- Aligned rule 10 and the intelligence standards on one public-source access rule that respects each site's terms and robots rules.
- Removed machine-specific Python paths, cookie paths and session dates. Detection now tries `python3 -c "import playwright"` and skips Layer 4 when the import fails.

## 1.3.0 - 2026-11-23

- Bundles the three shared reference files (intelligence standards, web access layers, layer 4 Playwright protocol), so the skill works without files outside the repo.

## 1.2.0 - 2026-11-23

- Cut the SKILL.md body from 809 lines to 229 lines.
- Added references/investigation-setup.md for setup, disambiguation, menus, tiers, web access and the folder tree.
- Added references/phase-playbook.md for the full step-by-step detail of Phases 0 to 11.
- Added references/ongoing-protocols.md for progress, the research log, confidence, saturation and refresh.
- Repointed SKILL.md at every reference file with a line saying when to read it.
- Bumped the version in plugin.json and SKILL.md frontmatter to 1.2.0.

## 1.1.3 - 2026-11-23

- Adds the marketplace icon approved by Daniel (thedanielmay/agent-tools#2).

## 1.1.2 - 2026-11-23

- Marketplace file gains a description, so the full check passes again (thedanielmay/agent-tools#10).

## 1.1.1 - 2026-11-22

- Added the marketplace files: marketplace.json, LICENSE and CHANGELOG.md.
- Added license and metadata.version to the SKILL.md frontmatter.
- Removed the email address from plugin.json, added the author url, homepage, repository and license, and set the plugin name to company-intel.
- Added the plugin install line to README.md and removed the version number from its prose.
- Added .gitignore.

## 1.1.0

- added a dependency check for expert-panel, document-skills:pdf, data-visualization and topic-intel.

## 1.0.0

- initial release with the anti-hallucination protocol (Cite-Before-You-Write, Numeric Quarantine, Fabrication Detection Pass), privacy checkpoint, adversarial search and Australian sources.
