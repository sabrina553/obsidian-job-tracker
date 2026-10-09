---
tags:
  - recruiters
name: Priya Shah
company: Meridian Talent
phone: 01632 960101
email: priya.shah@example.com
linkedin: https://example.com/in/priya-shah
first_contact: 2026-09-20
last_contact: 2026-10-06
next_follow_up: 2026-10-13
status: in conversation
---

# Priya Shah — Meridian Talent

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
| 2026-09-20 | LinkedIn | Introduced myself after applying to Lumen Medical | Send CV |
| 2026-09-23 | Call | 20-min alignment call: notice period, salary range, right to work | Wait for Lumen feedback |
| 2026-10-02 | Email | Put me forward for Pinecrest Analytics | Chase Pinecrest next week |
| 2026-10-06 | Call | Lumen stage 2 booked. Prep notes in the job note | Debrief after interview |

## Follow-Up Cadence
- Follow up once a week until you get a response.
- No response after 2 weeks → stop chasing, reach out to a different contact at Meridian Talent instead.
