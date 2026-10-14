---
entities:
- entity: booking
  shows:
  - Enter
  - Leave
- entity: area
  shows:
  - Name
entryPoints:
- web: /ui/admin/dashboard/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/dashboard.tsx
- kind: code
  role: implementation
  target: server/router/stats-router.go
---

# Dashboard

Counts of Users, Areas, Spaces and bookings and utilization figures for the Organization.
