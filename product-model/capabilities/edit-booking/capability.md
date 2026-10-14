---
availability:
- place: web::administration
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#update
- kind: code
  role: implementation
  target: ui/src/pages/admin/bookings/[id].tsx
---

# Edit booking

Change a booking's Space, times or subject, or the person it is for, from the administration's booking editor. The changed booking keeps to the same booking rules and slot check as a new one. Bookings visitors requested are never edited.
