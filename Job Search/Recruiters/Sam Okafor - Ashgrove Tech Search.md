---
tags:
  - recruiters
name: Sam Okafor
company: Ashgrove Tech Search
phone: 01632 960103
email: sam.okafor@example.com
linkedin: https://example.com/in/sam-okafor
first_contact: 2026-09-30
last_contact: 2026-09-30
next_follow_up: 2026-10-07
status: contacted
---

# Sam Okafor — Ashgrove Tech Search

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
| 2026-09-30 | LinkedIn | Connection request + intro message | Follow up in 1 week |

## Follow-Up Cadence
- Follow up once a week until you get a response.
- No response after 2 weeks → stop chasing, reach out to a different contact at Ashgrove Tech Search instead.
