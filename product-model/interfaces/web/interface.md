---
type: web
actors:
- user
- visitor
- kiosk
entryPoints:
- web: /ui/search/
- web: /ui/admin/
- web: /ui/login/
references:
- kind: code
  role: implementation
  target: server/app/app.go
- kind: code
  role: implementation
  target: server/router/unauthorized-routes.go
- kind: doc
  role: context
  target: README.md
---

# Seatsurfing web app

The browser app Seatsurfing serves under /ui: the Booking Site where Users book and see their bookings, installable on phones, the administration area for Users whose Roles grant any administrative access, and the pages reached without signing in: sign-in, password reset and invitations, public booking and kiosk displays.
