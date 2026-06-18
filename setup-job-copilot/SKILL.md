---
name: setup-job-copilot
description: Bootstrap a personal, self-improving "Job Hunt Copilot" for a user from scratch. Use this skill whenever someone wants to set up a resume-tailoring or job-search system, says anything like "set up a job search system", "build me a job hunt copilot", "help me create a resume system", "I want Claude to tailor my resume to jobs", "set up the job copilot", or asks to replicate a system that customises resumes per job and learns over time. This skill interviews the user, builds their folder of living source files (achievement bank, format rules, search config, signal log, hypotheses, confirmed patterns, keyword ledger, resume library, tracker), then creates a reusable resume-tailoring skill and a self-improving learning loop. Trigger even if the user only describes the outcome (e.g. "I keep rewriting my resume for every job and want to automate it") without naming the system.
---

# Setup Job Copilot

Bootstrap a complete, personal job-search system for the user: a folder of living source files,
a reusable "tailor my resume" skill, and a self-improving learning loop that gets sharper with
every application. Run it in stages and confirm each stage before moving on — the user's real
answers are the whole point, so don't rush past the interview into generic templates.

The mental model: the user maintains a small set of living files (their source of truth). A skill
reads them fresh every time they paste a job description and produces a tailored resume + cover
letter. Every application outcome (ATS rejection, callback, interview, no-offer) is logged as a
labelled data point, so the system learns which roles, framings, and keywords actually work.

---

## Stage 1 — Interview the user

Before creating anything, ask one focused batch of questions (not 20 separate turns). If the user
has already shared a resume or files, extract everything you can from them first and only ask for
the gaps. Cover:

1. **Background** — years of experience, current/recent roles, domains worked in, and the role +
   seniority being targeted.
2. **Constraints** — target locations (remote / cities / open to relocation), minimum salary,
   company stage/size preferences, and hard exclusions (industries, role types, or title levels
   too junior or too senior).
3. **Proof** — biggest achievements with real numbers (revenue, growth, scale, users, team size).
   Push for metrics; these become the achievement bank.
4. **Materials** — an existing resume, prior tailored resumes, and a writing sample whose voice
   the cover letters should match. Ask them to share or point to these.

Confirm a summary of what you heard before building.

---

## Stage 2 — Build the folder of living files

Create a working folder and populate the files below using the user's real answers. Where an
answer is missing, leave a clearly-marked `TODO`. Tell the user these files are theirs and are the
source of truth — the system reads them fresh on every run, so they should keep them current.

Read `references/file-templates.md` for the structure and section breakdown of each file. Build:

1. `profile.md` — achievement bank (who they are, career timeline, achievement bullets WITH
   NUMBERS grouped by theme, Core Strengths, a "What Makes Me Stand Out" section of 5-8 angles
   tagged by the role/company each suits, and a Metric Notes table for conflicting numbers). The
   only source of resume metrics.
2. `resume-format.md` — document format spec (derived from their best existing resume — note its
   path as the "gold standard"), section order, per-section writing rules, a tailoring checklist,
   file-naming + save conventions, and their writing rules / things to avoid.
3. `search-config.md` — target titles, locations, domains, deprioritised domains, include/exclude
   keywords, salary floor + target, a title-band filter, and scoring notes.
4. `boards-and-companies.md` — tiered job boards, target companies grouped by domain with
   career-page URLs, and an Active Applications & Contact History section.
5. `learnings-log.md` — append-only dated signal log with a format block at the top.
6. `hypotheses.md` — Apply and Callback hypotheses, each with status (Forming / Confirmed /
   Disproved) and an evidence list. 3+ consistent data points graduates a hypothesis.
7. `search-patterns.md` — confirmed patterns promoted from hypotheses (confidence, evidence,
   implication) plus a Config Change History table.
8. `keyword-ledger.md` — the resume-effectiveness brain. A per-application table (company, role,
   resume variant, keywords/framings led with, outcome) plus a "what's working / what's not"
   summary. Treat ATS rejections and callbacks as labelled training data.
9. `/Resume RAG/` — a library of prior tailored resumes (as text) plus a short index so the system
   can find the closest prior resume to a new role and reuse proven language. Seed with whatever
   the user shares.
10. A **tracker** — a roles table the user can see at a glance (markdown table, CSV, Notion, or
    spreadsheet — match their tools). Columns: Role, Company, Status, Score, Location, Salary,
    Link, Date Found, Why It Fits, Concerns, plus three learning columns filled in later: Why I
    Applied, Confirmed Signal, Notes.

---

## Stage 3 — Build the "tailor my resume" skill

Create a reusable resume-tailoring skill for the user. If a skill-packaging tool is available,
package it as an installable `.skill` file and present it; otherwise deliver a `SKILL.md` they can
save. The skill should trigger whenever the user gives a JD and asks for a tailored resume or cover
letter, and when it runs it should:

a. Take a JD as pasted text, a URL (fetch it), or a file.
b. Read `profile.md`, `resume-format.md`, `search-config.md`, `search-patterns.md`,
   `hypotheses.md`, and `keyword-ledger.md` — always the live versions, never from memory.
c. Find the 1-2 closest prior resumes in `/Resume RAG/` and reuse phrasing that worked.
d. Analyse the JD (title, domain keywords, seniority, must-haves), score the fit, and flag honest
   gaps — never invent achievements or metrics.
e. Build the resume per `resume-format.md` (use a docx-generation skill if available), run the
   tailoring checklist, and write a cover letter in the user's voice.
f. Save the DOCX + PDF (and cover letter) to a per-company folder with the naming convention.
g. Log the application to `learnings-log.md` and add a row to `keyword-ledger.md`.

See `references/resume-tailor-skill.md` for a ready-to-adapt SKILL.md body for this sub-skill.

---

## Stage 4 — Close the loop (self-improving)

Set up a lightweight recurring routine — a checklist the user can run, or a scheduled task if the
environment supports one — that does a "learning pass":

- Review the tracker for status changes since last time.
- For each ATS rejection, callback, interview, or no-offer: write a dated signal to
  `learnings-log.md` and update `keyword-ledger.md` (did the keywords/framing help or hurt?).
- Generate or update hypotheses in `hypotheses.md` from the new evidence.
- Promote any hypothesis with 3+ consistent data points to `search-patterns.md`, and update
  `search-config.md` if a confirmed pattern implies a change (log the change + reason).
- When a tailored resume earns a callback, extract the winning keywords/highlights and feed them
  back into `profile.md` and `keyword-ledger.md` so future resumes lead with what works.

Explain to the user that this is what makes the system valuable: every application is a labelled
data point, so the resumes get sharper over time.

---

## Principles (apply throughout)

- **Truthful tailoring only.** Reframe and reorder real achievements; never fabricate a metric,
  employer, or responsibility.
- **Living files are the source of truth** — read them fresh each run, keep them updated.
- **Verify listings are live** before treating them as real (fetch the ATS URL; don't trust
  aggregator links for recency).
- **Explain your reasoning** when scoring or positioning a role, so the user can correct the system.
- **Match the user's tools.** Markdown folder, Notion, or a spreadsheet — build where they already work.
