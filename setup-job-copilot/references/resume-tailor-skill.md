# Ready-to-adapt: the "resume-tailor" sub-skill

Use this as the body of the resume-tailoring skill you create for the user in Stage 3. Replace the
folder path with the user's actual working folder, and adjust file names if you named them
differently. Keep the description "pushy" so it triggers reliably.

---

```markdown
---
name: resume-tailor
description: Tailor [USER]'s resume and cover letter to a specific job description. Use whenever
  [USER] provides a job description (pasted text, a posting URL, or a file) and wants a resume
  customised for it, or says "tailor my resume", "write me a resume for this role", "customise my
  CV", "make a resume for [company]", or "draft a cover letter for this". Trigger even if they
  don't say the word "resume" but clearly want an application document. Reads [USER]'s living
  profile, format rules, and prior-resume library so it always uses the current achievement bank.
---

# Resume Tailor — [USER]

Turn a job description into a tailored resume (DOCX + PDF) and matching cover letter, built from
[USER]'s real achievement bank and format rules. Never invent achievements or metrics — if the JD
wants something not in their background, name it as a gap.

## Source of truth — read first, every run
Working folder: [PATH TO USER'S FOLDER]
- resume-format.md — format spec + writing rules + tailoring checklist (read in full)
- profile.md — achievement bank; the only source of bullets/metrics (cross-check the Metric Notes table)
- search-patterns.md + hypotheses.md — positioning lens (what to emphasise / downplay)
- keyword-ledger.md — which keywords/framings have earned callbacks vs ATS rejections; lead with what works
- /Resume RAG/ — start at the index, read the 1-2 closest prior resumes, reuse proven phrasing
- Gold-standard DOCX template: [PATH] — match its font/margins/sizes

If the folder isn't accessible, say so and ask the user to paste the files — don't guess.

## Workflow
1. Get the JD (fetch if a URL; if the page is client-rendered and returns an empty shell, ask for the text). Capture the exact title + company.
2. Read the source files; pick the closest prior resume(s) from /Resume RAG/.
3. Analyse the JD: required experience, domain keywords, seniority, must-haves; score the fit; flag gaps honestly.
4. Build sections per resume-format.md (Executive Summary mirrors JD keywords, no company names/metrics; Selected Highlights bold-label format, ordered by relevance; Experience bullets action-verb-first). Use the docx skill to generate, matching the gold-standard template.
5. Run the tailoring checklist; fix anything failing.
6. Write a short cover letter in the user's voice (load their voice skill if they have one).
7. Save DOCX + PDF + cover letter to [Resume]/[Company]/ with the naming convention; present the files and a 2-3 line summary (angle led with, highlights chosen, gaps to prep). Log the application to learnings-log.md and add a row to keyword-ledger.md.

## Principles
- Truthful tailoring; reframe real achievements, never fabricate.
- Answer the JD then sell: summary feeds the ATS, highlights sell the fit.
- Borrow proven language from the RAG library; lead with what the keyword ledger says works.
- Quiet bar: would a tired recruiter, skimming 20 seconds, see why this person fits THIS role?
```
