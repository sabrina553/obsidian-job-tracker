---
tags:
  - job-searches
---

# Job Search Process

The end-to-end workflow this vault is built around. Two parallel tracks — **applications** and **recruiters** — feed the same [[Job Tracker]].

## Application Track

```
Find → Copy details → Research → Adjust CV/Cover → Apply → Track → Follow up
```

1. **Find** — search job boards (LinkedIn, Reed, Glassdoor, CV-Library and others). Add anything promising to [[Prospective Jobs]] first if you don't have time to action it immediately.
2. **Copy the details** — create a note from [[Templates/Job Application|the Job Application template]] (create a new note inside `Applications/`, or `Ctrl/Cmd+P → Templater: Create new note from template`). It'll prompt you for company, role, URL, source and recruiter, then rename itself `DDMMYY-Company-Role` and file itself into this week's folder (e.g. `Applications/2026-W41/`). Paste the full listing into the Job Description section — listings disappear once filled, and you'll want it for interview prep.
3. **Research** — fill in Company Research: what they do, recent projects/news (LinkedIn, Glassdoor, company blog), and anything culture-related. Pull out 3–5 points from the listing for your Personal Statement Angle — remember, the personal statement is the **who**, not the how.
4. **Adjust CV/Cover** — use [[CV-Cover-Prompt]] against the tailored job note to prioritise skills the listing calls out and skills you have strong evidence for. Keep it chronological, two pages CV / one page cover.
5. **Apply** — submit, then tick off the Application Checklist in the note.
6. **Track** — set `status: applied` and fill `date_applied` in the note's properties. That's it: [[Job Tracker]] picks it up automatically.
7. **Follow up** — if there's a direct contact and ~1 week has passed with no reply, send the [[Email Templates#Application — Post-Apply Follow-Up|post-apply follow-up]]. Log every touchpoint in the note's Follow-Up Log.

**Weekly target:** apply to at least **7–10 roles**.

## Recruiter Track

```
Identify → Reach out → Log → Follow up weekly → 2-week rule
```

1. **Identify** 3+ recruiters/agencies per week working roles in your target areas.
2. **Reach out** using the [[Email Templates#Recruiter — Initial Outreach|initial outreach template]], referencing a specific role you've applied to through them.
3. **Log** the contact by creating a note in `Recruiters/` (the [[Templates/Recruiter Contact|Recruiter Contact]] template fills in the rest). It appears in [[Recruiters]] automatically.
4. **Follow up** weekly using the [[Email Templates#Recruiter — Weekly Follow-Up|follow-up template]] until you get a response.
5. **2-week rule** — no response after 2 weeks of chasing → stop, and reach out to a different contact at the same company instead.

Full detail lives in [[Recruiters#Weekly Recruiter Loop]].

## Weekly Rhythm

An example week. Rearrange it around your own schedule:

| Day | Focus |
| --- | ----- |
| Mon | Check schedule/conflicts, organise the week's applications, interview prep (STARR, 2/day) |
| Tue | Apply to top-choice roles, work on your skills/STARR document |
| Wed | Check emails, apply to roles, contact/follow up with recruiters |
| Thu | Skills training, apply to roles |
| Fri | Skills/STARR work, contact/follow up with recruiters |
| Sat | Tailor applications for the most promising roles |
| Sun | Check emails, plan the week ahead |

End each weekday by updating [[Job Tracker]] / [[Recruiters]] and noting anything to follow up on tomorrow.

## Interview Prep

[[Interview Prep]] has the full etiquette checklist, answer formulas (Hook/Past/Present/Future for general questions, mini-STARR for strength/technical, full STARR for behavioural) and a question bank to draft against. Log real interview questions/answers in the relevant job note's Interview Notes section so they can be reused.

## How the Tracker Works

`Applications/Jobs.base` picks up every note tagged `job-applications` and builds views from its properties: Kanban Board, Needs Follow-Up, This Week's Applications, Interviewing, Not Yet Applied, Declined / Rejected, Offers and Everything. Nothing is maintained by hand. Change `status`, `date_applied` and so on in a job note and every view updates.

`status` values: `not-applied` · `applied` · `interview` · `offer` · `rejected` · `declined`. Matching is forgiving, so `Rejected (after interview)` still lands in the right column.

`Recruiters/recruiters.base` does the same for notes tagged `recruiters`, and each recruiter note embeds a table of every job that links to it (through the job's `recruiter` property).
