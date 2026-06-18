# Job Hunt Copilot — Claude Skill

![Job Hunt Copilot cover](assets/cover.svg)

A Claude Code skill that bootstraps a complete, self-improving job-search system for Product Managers (or any senior individual contributor). One conversation sets up everything; every application after that makes the system smarter.

---

## What it does

When you run this skill, Claude interviews you, then builds:

1. **A folder of living source files** — your achievement bank, format rules, search config, keyword ledger, hypothesis tracker, and a library of prior tailored resumes.
2. **A reusable resume-tailoring sub-skill** — paste any job description and get a tailored resume + cover letter built from your real achievement bank, not generic filler.
3. **A self-improving learning loop** — every outcome (ATS rejection, callback, interview, no-offer) is logged and fed back into the system so your resumes get sharper over time.

---

## Installation

**Option 1 — install the packaged skill file (recommended)**

```bash
claude skill install https://github.com/deewang/product-manager-resume-writing-skill/raw/main/setup-job-copilot.skill
```

**Option 2 — clone and install locally**

```bash
git clone https://github.com/deewang/product-manager-resume-writing-skill.git
cd product-manager-resume-writing-skill
claude skill install ./setup-job-copilot.skill
```

---

## How to trigger it

Once installed, say any of the following in a Claude Code conversation:

- `"Set up a job search system for me"`
- `"Build me a job hunt copilot"`
- `"Help me create a resume system"`
- `"I want Claude to tailor my resume to jobs"`
- `"Set up the job copilot"`
- `"I keep rewriting my resume for every job — help me automate it"`

Claude will start Stage 1 (the interview) automatically.

---

## What gets created

After the setup conversation, you'll have a working folder containing:

| File | Purpose |
|------|---------|
| `profile.md` | Achievement bank — every bullet and metric, grouped by theme. The only source of resume content. |
| `resume-format.md` | Document spec, section order, writing rules, and pre-save tailoring checklist. |
| `search-config.md` | Target titles, locations, salary floor, include/exclude keywords for job searching. |
| `boards-and-companies.md` | Tiered job boards and a target company list with career-page URLs. |
| `learnings-log.md` | Append-only dated log of every meaningful outcome signal. |
| `hypotheses.md` | Apply and callback hypotheses (Forming → Confirmed → Promoted). |
| `search-patterns.md` | Confirmed patterns promoted from hypotheses, with implication notes. |
| `keyword-ledger.md` | The self-improving brain: which keywords/framings earned callbacks vs ATS rejections. |
| `/Resume RAG/` | Library of prior tailored resumes as text, with an index for fast retrieval. |
| `roles-tracker` | Role pipeline table (markdown, CSV, or Notion — matching your tools). |

A **`resume-tailor` sub-skill** is also created and installed. After setup, paste any job description and say `"tailor my resume"` — it reads your living files fresh every time and produces a tailored resume and cover letter.

---

## The ongoing loop

After each application:

1. Log the outcome in your tracker.
2. Run the learning pass (ask Claude to `"do a learning pass on my job search"`): signals go into `learnings-log.md`, hypotheses get updated, confirmed patterns get promoted to `search-patterns.md`.
3. When a resume earns a callback, the winning keywords flow back into `keyword-ledger.md` and `profile.md` — so future resumes lead with what actually works.

---

## Principles

- **Truthful tailoring only.** Real achievements reframed; no invented metrics or employers.
- **Living files are the source of truth.** Claude reads them fresh on every run.
- **Every application is a labelled data point.** The system learns which roles, framings, and keywords work for you specifically.

---

## Skill files

```
setup-job-copilot.skill              # Packaged installable skill
setup-job-copilot/
  SKILL.md                           # Skill source
  references/
    file-templates.md                # Structure for each living file
    resume-tailor-skill.md           # Ready-to-adapt sub-skill body
```
