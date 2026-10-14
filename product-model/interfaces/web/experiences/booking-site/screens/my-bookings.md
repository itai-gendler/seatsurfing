---
entities:
- entity: booking
  shows:
  - Space
  - Enter
  - Leave
  - Subject
- entity: area
  shows:
  - Name
entryPoints:
- web: /ui/bookings/
references:
- kind: code
  role: implementation
  target: ui/src/pages/bookings.tsx
- kind: code
  role: implementation
  target: server/service/booking-service.go#GetUpcomingBookingsForUser
---

# My bookings

The User's own bookings that have not ended yet, each marked when it still waits for approval or belongs to a recurring series, with its calendar file and cancelling one booking or all upcoming bookings of its series.
