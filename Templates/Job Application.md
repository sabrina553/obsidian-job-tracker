<%*
// Where application notes live. Change this if you rename the folder.
const APPLICATIONS_FOLDER = "Job Search/Applications";

const existing = tp.frontmatter;
const alreadyFilled = existing && existing.company;
const company = alreadyFilled ? existing.company : await tp.system.prompt("Company Name");
const role = alreadyFilled ? existing.role : await tp.system.prompt("Job Title");
const jobUrl = alreadyFilled ? existing.job_url : await tp.system.prompt("Job Listing URL (Leave Blank if None)", "");
const source = alreadyFilled ? existing.source : await tp.system.suggester(
  ["LinkedIn", "CV-Library", "Glassdoor", "Reed", "Indeed", "Recruiter Referral", "Company Site", "Other"],
  ["LinkedIn", "CV-Library", "Glassdoor", "Reed", "Indeed", "Recruiter Referral", "Company Site", "Other"],
  false, "Where Did You Find This Listing?"
);
const viaRecruiter = alreadyFilled ? existing.via_recruiter : await tp.system.suggester(
  ["Yes", "No"], [true, false], false, "Was This Application via a Recruiter?"
);
// If it came via a recruiter, offer to link one of your recruiter notes
let recruiter = alreadyFilled && existing.recruiter ? `"${existing.recruiter}"` : "";
if (!alreadyFilled && viaRecruiter) {
  const recruiterNotes = app.vault.getMarkdownFiles().filter(f =>
    [].concat(app.metadataCache.getFileCache(f)?.frontmatter?.tags ?? []).includes("recruiters"));
  if (recruiterNotes.length) {
    const picked = await tp.system.suggester(
      ["(None / add later)", ...recruiterNotes.map(f => f.basename)],
      [null, ...recruiterNotes], false, "Which Recruiter?");
    if (picked) recruiter = `"[[${picked.basename}]]"`;
  }
}
-%>
---
tags:
  - job-applications
company: <% company %>
role: <% role %>
job_url: <% jobUrl %>
source: <% source %>
via_recruiter: <% viaRecruiter %>
date_found: <% tp.date.now("YYYY-MM-DD") %>
date_applied:
status: not-applied  # not-applied | applied | interview | offer | rejected | declined
interview_stage:
recruiter: <% recruiter %>
cv_version:
location:
salary:
---

# <% role %> — <% company %>

## Job Description

> Paste the full listing here verbatim (responsibilities, required skills, desirable skills) — listings get taken down and you'll want this for interview prep later.

## Key Skills Called Out

## Desirable / Bonus Skills

## Company Research

- What they do:
- Recent projects / news:
- Culture notes (Glassdoor / LinkedIn / socials):

## Personal Statement Angle

_Who I am and how I align. Pick 3–5 points from the listing that speak to my experience. The personal statement is the **who**, not the how._

1.
2.
3.

## CV / Cover Letter Adjustments

- CV version used:
- Key changes made for this role:

## Application Checklist

- [ ] Job description copied above
- [ ] Company research done
- [ ] CV tailored (see [[CV-Cover-Prompt]] for the adjustment prompt)
- [ ] Cover letter tailored
- [ ] Applied
- [ ] Status and date_applied updated
- [ ] Confirmation email saved

## Follow-Up Log

|Date|Action|Notes|
|---|---|---|
||||

## Interview Notes

<%*
if (!alreadyFilled) {
  // Rename to DDMMYY-Company-Role and file it under a weekly folder, e.g. 2026-W41
  const clean = (str) => str.replace(/[\\/:*?"<>|#^\[\]]/g, "").trim();
  const fileName = `${tp.date.now("DDMMYY")}-${clean(company)}-${clean(role)}`;
  const week = tp.date.now("GGGG-[W]WW");
  await tp.file.move(`${APPLICATIONS_FOLDER}/${week}/${fileName}`);
}
-%>