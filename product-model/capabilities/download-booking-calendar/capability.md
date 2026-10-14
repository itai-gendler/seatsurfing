---
availability:
- place: web::booking-site
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#getIcal
- kind: code
  role: implementation
  target: server/router/recurring-booking-router.go#getIcal
- kind: code
  role: implementation
  target: ui/src/components/Ical.ts
---

# Download booking calendar

Download a calendar file of one's own booking, or of every occurrence of one's series, to add it to any calendar.
