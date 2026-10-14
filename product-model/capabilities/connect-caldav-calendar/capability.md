---
availability:
- place: web::booking-site
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/user-preferences-router.go#caldavListCalendars
- kind: code
  role: implementation
  target: server/router/booking-router.go#getCalDavConfig
---

# Connect CalDAV calendar

Connect one's own CalDAV calendar so that one's bookings appear in it as they are made, changed, approved and cancelled.
