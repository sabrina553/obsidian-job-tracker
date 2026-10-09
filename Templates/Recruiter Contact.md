<%*
const existing = tp.frontmatter;
const alreadyFilled = existing && existing.name;

const name = alreadyFilled ? existing.name : await tp.system.prompt("Recruiter name");
const company = alreadyFilled ? existing.company : await tp.system.prompt("Agency / company");
-%>
---
tags:
  - recruiters
name: <% name %>
company: <% company %>
phone:
email:
linkedin:
first_contact: <% tp.date.now("YYYY-MM-DD") %>
last_contact: <% tp.date.now("YYYY-MM-DD") %>
next_follow_up: <% tp.date.now("YYYY-MM-DD", 7) %>
status: contacted
---

# <% name %> — <% company %>

## Roles Discussed

```base
filters:
  and:
    - file.hasTag("job-applications")
    - file.hasLink(this.file)
properties:
  file.name:
    displayName: Application
  company:
    displayName: Company
  role:
    displayName: Role
  status:
    displayName: Status
  date_found:
    displayName: Found
  date_applied:
    displayName: Applied
  interview_stage:
    displayName: Interview Stage
views:
  - type: table
    name: Jobs via this recruiter
    order:
      - file.name
      - company
      - role
      - status
      - date_found
      - date_applied
      - interview_stage
    sort:
      - property: date_found
        direction: DESC
```

## Contact Log
| Date | Type (call/email/LinkedIn) | Notes | Next Step |
| ---- | --------------------------- | ----- | --------- |
| <% tp.date.now("YYYY-MM-DD") %> | Initial outreach | | Follow up in 1 week |

## Follow-Up Cadence
- Follow up once a week until you get a response.
- No response after 2 weeks → stop chasing, reach out to a different contact at <% company %> instead.
<%*
if (!alreadyFilled) {
  const clean = (str) => str.replace(/[\\/:*?"<>|#^\[\]]/g, "").trim();
  await tp.file.rename(`${clean(name)} - ${clean(company)}`);
}
-%>