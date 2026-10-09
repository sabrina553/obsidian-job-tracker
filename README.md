# Obsidian Job Tracker

An Obsidian vault template for running a job search: one note per application, one note per recruiter, and live dashboards built with [Bases](https://help.obsidian.md/bases) that update themselves as you go. New notes are created through [Templater](https://github.com/SilentVoid13/Templater) prompts, so you never fill in frontmatter by hand.

It comes with fictional sample data so you can see every view populated straight away.

## Features

- **Kanban board** of every application, grouped by stage: Not Applied → Applied → Interviewing → Offer → Closed. Closed cards drop off after 14 days untouched.
- **Needs Follow-Up** view: applications still waiting for a reply 7+ days after you applied.
- More views: This Week's Applications, Interviewing, Not Yet Applied, Declined / Rejected, Offers, Everything.
- **Guided job note creation**: Templater asks for company, role, URL, source and recruiter, then names the note `DDMMYY-Company-Role` and files it into a weekly folder (`Applications/2026-W41/`).
- **Recruiter CRM** with a computed *Action* column: Waiting, Follow up today, Follow-up overdue, Switch contact (after 2 weeks of silence), Active.
- **Two-way recruiter links**: set a job's `recruiter` property and that job appears in a table on the recruiter's note.
- **Reference notes**: an end-to-end process, email templates (outreach, follow-up, thank-you), an interview prep library (STARR, Hook/Past/Present/Future, question banks) and a CV-tailoring AI prompt.

## Requirements

- [Obsidian](https://obsidian.md) **1.10 or later**, with the core Bases plugin (enabled in this vault).
- [Templater](https://github.com/SilentVoid13/Templater) community plugin. Its settings are already included.

## Setup

1. **Get the vault**: click **Use this template** on GitHub (or clone / download the ZIP).
2. **Open it in Obsidian**: *Open folder as vault* and choose the folder. When asked, choose **Trust author and enable plugins**.
3. **Install Templater**: *Settings → Community plugins → Browse*, search for **Templater**, then **Install** and **Enable**. It picks up the bundled settings automatically.
4. **Turn on the file-creation trigger**: *Settings → Templater → Trigger Templater on new file creation*. Templater keeps this setting on each device for security, so a template can't switch it on for you.
5. Open **`Job Search/Job Tracker.md`**. It's also bookmarked.

## Folder Structure

```
Job Search/
├── Job Tracker.md          ← dashboard: follow-ups, kanban, recruiters
├── Job Search Process.md   ← the end-to-end workflow
├── Prospective Jobs.md     ← quick shortlist of listings to look at later
├── Email Templates.md
├── Interview Prep.md
├── CV-Cover-Prompt.md
├── Applications/
│   ├── Jobs.base           ← all the application views
│   └── 2026-W41/           ← one folder per week, created automatically
│       └── 081026-Northgate Rail-Embedded Linux Engineer.md
└── Recruiters/
    ├── Recruiters.md       ← recruiter dashboard + weekly loop
    ├── recruiters.base
    └── Priya Shah - Meridian Talent.md
Templates/
├── Job Application.md
└── Recruiter Contact.md
```

## Usage

### Add a Job

Create a new note anywhere inside `Job Search/Applications/`, or run **Templater: Create new note from template → Job Application** from the command palette. Answer the prompts, paste in the listing, and work down the checklist.

As the application moves along, update its properties:

| Property | Values / format |
| --- | --- |
| `status` | `not-applied` · `applied` · `interview` · `offer` · `rejected` · `declined` |
| `date_applied` | `YYYY-MM-DD`. Drives "Needs Follow-Up" and "This Week". |
| `interview_stage` | Free text, e.g. `Stage 2: technical` |
| `recruiter` | A link to a recruiter note, e.g. `"[[Priya Shah - Meridian Talent]]"` |
| `cv_version`, `location`, `salary` | Free text |

Matching on `status` is forgiving. Anything containing "reject" or "decline" counts as Closed, and anything containing "interview" counts as Interviewing, so `Rejected (after stage 2)` works fine.

### Add a Recruiter

Create a new note in `Job Search/Recruiters/`. The template asks for their name and agency, then sets `first_contact`, `last_contact` and `next_follow_up` (+7 days). Keep those dates and `status` up to date and the Action column tells you who to chase.

Recruiter `status` values: `contacted` · `replied` · `in conversation` · `interviewing` · `no response - moved on`

## Sample Data

All companies, people, emails (`example.com`), phone numbers (Ofcom's reserved drama range) and listings are fictional. Any resemblance to real organisations or people is coincidental.

The samples are dated September–October 2026. Date-relative views such as "This Week's Applications" and "Contacted this week" will empty out as time passes, which is expected.

When you're ready to start for real, delete the week folders under `Applications/` and the person notes under `Recruiters/`. Keep the `.base` files and `Recruiters.md`.

## Customising

- **Rename or move folders**: update the regex paths in *Settings → Templater → File regex templates*, and `APPLICATIONS_FOLDER` at the top of `Templates/Job Application.md`.
- **Job sources**: edit the list in the `source` prompt in `Templates/Job Application.md`.
- **Follow-up thresholds**: the 7-day and 14-day rules are filters and formulas in `Jobs.base` and `recruiters.base`. Open the file in a text editor, or change a view's filters from the Bases toolbar.
- **Kanban as real columns**: the board is a Bases *cards* view grouped by stage. For a drag-and-drop board, the optional **Kanban Bases View** community plugin can group the same base by `formula.stage`.

## License

[MIT](LICENSE): use it, fork it, adapt it for your own search.
