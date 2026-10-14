---
availability:
- place: web::administration
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#getPresenceReport
- kind: code
  role: implementation
  target: ui/src/pages/admin/report/analysis.tsx
---

# View presence report

See which person was booked in on which day of a period of up to 31 days, for one Area or all, and download it. It takes Presence report access Read and is withheld from everyone while the Organization hides reports.
