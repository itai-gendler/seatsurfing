---
availability:
- place: web::administration
references:
- kind: code
  role: implementation
  target: server/router/stats-router.go
- kind: code
  role: implementation
  target: ui/src/pages/admin/dashboard.tsx
---

# View statistics

See the Organization's dashboard: how many Users, Areas, Spaces and bookings there are, bookings today, yesterday and this week, utilization against the target and bookings by weekday, per Area or for all. It takes Analytics access Read and is withheld from everyone while the Organization hides statistics.
