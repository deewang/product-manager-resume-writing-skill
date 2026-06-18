# File templates — structure for each living file

Adapt these to the user's domain and tools. Headings are a guide, not a straitjacket — keep what
serves the user, drop what doesn't. Every file should open with a one-line note on its purpose and
how the system uses it.

---

## profile.md (achievement bank)

- **Who I am** — 2-3 lines for job matching: years of experience, domains, IC vs manager, what they deliver.
- **Career timeline** — table: Period | Company | Role | Domain.
- **Top achievements (with numbers)** — bullets grouped by theme (e.g. Revenue, Product, Growth, Leadership). Each bullet is a standalone proof point with a real metric.
- **Extended achievements bank** — additional/variant bullets surfaced from prior resumes.
- **Metric Notes table** — | Metric | Canonical value | Variants seen | Recommended | — the tie-breaker for any number stated differently across versions. This is the only source of resume metrics.
- **Core Strengths** — skills mapped to real shipped work, grouped (domains / skills / leadership / markets).
- **What Makes Me Stand Out** — 5-8 distinct angles, each tagged with the role/company type it suits best.
- **What I'm NOT looking for** — quick filters for bad-fit roles.

## resume-format.md

- **Document format** — table: font, margins, name/contact/header sizes, body size, bullet indent + character. Note the path to the user's "gold standard" resume as the format reference.
- **Section structure** — the ordered list of sections.
- **Writing rules, section by section** — Executive Summary (answer the JD, keywords, no company names, no metrics), Selected Highlights (bold-label format, 4-6, ordered by relevance), Experience bullets (action verb first, metric as participial phrase).
- **Sentence & word rules** — economy, clarity, active voice, numerals for metrics, things to avoid (no "responsible for", no em-dashes, no "→", one idea per bullet).
- **Tailoring checklist** — the pre-save checks.
- **File naming + folder structure** — naming convention and where files are saved; always export a PDF for submission, keep the DOCX for edits.

## search-config.md

- Target roles, target locations, domain preferences, deprioritised domains.
- Keywords to INCLUDE / EXCLUDE in job descriptions.
- Salary floor + target. Title-band filter (too-junior floor, too-senior ceiling).
- Scoring + filtering notes for the search agent.

## boards-and-companies.md

- **Job boards**, tiered: Tier 1 reliable ATS boards (verify listings live here), Tier 2 aggregators (discover then verify at source), Tier 3 niche/curated.
- **Companies to check directly**, grouped by domain, with career-page URLs.
- **Active Applications & Contact History** — where the user has applied or has a contact.
- **Notes for the search agent** — verification rules (fetch the ATS URL; don't trust aggregator recency).

## learnings-log.md

- A format block at the top: `### YYYY-MM-DD / Signal type / Role / Signal / Action taken`.
- Append-only, dated entries for every meaningful event.

## hypotheses.md

- Status key: Forming (1-2 points) / Confirmed (3+, promoted) / Disproved / Mixed.
- **Apply hypotheses** (what draws the user to apply) and **Callback hypotheses** (why companies call back), each with evidence-for / evidence-against and notes.
- A Disproved/Retired section.

## search-patterns.md

- Confirmed patterns promoted from hypotheses, each with: Pattern, Confidence, Evidence, Implication.
- Sections for Domain patterns, Role/Company patterns, Apply patterns, Callback patterns, Anti-patterns.
- A **Config Change History** table: | Date | Change | Reason |.

## keyword-ledger.md (the self-improving brain)

- **Application ledger** table: | Date | Company | Role | Resume variant / lead framing | Key keywords led with | Outcome | Read |.
- Outcome legend: ATS Rejected / Callback / Interview / Offer / No Offer / Pending / Pass.
- **What's working** (lead with these) and **What's not working** (stop leading with these) summaries.
- **Open watch-items** — clusters to watch (e.g. repeated ATS rejections sharing a keyword/domain).

## /Resume RAG/

- A subfolder of prior tailored resumes saved as text/markdown.
- A short `00_index.md` listing each resume by target role/domain so the closest match is easy to find.

## Tracker (table / Notion / spreadsheet)

- Columns: Role, Company, Status, Score, Location, Salary, Link, Date Found, Why It Fits, Concerns,
  Why I Applied, Confirmed Signal, Notes.
- Status options: Found / Shortlist / Researching / Applied / Phone Screen / Interviewing / Offer /
  ATS Rejected / Interview Rejected / Pass / No Offer.
