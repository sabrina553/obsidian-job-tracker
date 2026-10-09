---
tags:
  - recruiters
name: Jordan Reyes
company: Bluebell Recruitment
phone: 01632 960104
email: jordan.reyes@example.com
linkedin: https://example.com/in/jordan-reyes
first_contact: 2026-09-21
last_contact: 2026-09-28
next_follow_up: 2026-10-05
status: contacted
---

# Jordan Reyes — Bluebell Recruitment

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
| 2026-09-21 | Email | Initial outreach | Follow up in 1 week |
| 2026-09-28 | Email | Weekly follow-up, no reply | 2-week rule hits on 2026-10-05: try someone else at Bluebell |

## Follow-Up Cadence
- Follow up once a week until you get a response.
- No response after 2 weeks → stop chasing, reach out to a different contact at Bluebell Recruitment instead.
