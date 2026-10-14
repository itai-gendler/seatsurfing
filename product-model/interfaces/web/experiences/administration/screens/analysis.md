---
entities:
- entity: booking
  shows:
  - Booker
  - Enter
- entity: area
  shows:
  - Name
entryPoints:
- web: /ui/admin/report/analysis/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/report/analysis.tsx
- kind: code
  role: implementation
  target: server/router/booking-router.go#getPresenceReport
---

# Analysis

The presence report: which person was booked in on which day of a chosen period of up to 31 days, optionally for one Area.
