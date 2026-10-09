---
tags:
  - recruiters
name: Alex Morgan
company: Signal Path Recruitment
phone: 01632 960102
email: alex.morgan@example.com
linkedin: https://example.com/in/alex-morgan
first_contact: 2026-09-29
last_contact: 2026-10-01
next_follow_up: 2026-10-08
status: replied
---

# Alex Morgan — Signal Path Recruitment

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
| 2026-09-29 | Email | Applied to Orbitra via their listing, sent intro email | Follow up in 1 week |
| 2026-10-01 | Email | Replied: Orbitra keen, recruiter screen to be booked | Wait for screen date |

## Follow-Up Cadence
- Follow up once a week until you get a response.
- No response after 2 weeks → stop chasing, reach out to a different contact at Signal Path Recruitment instead.
