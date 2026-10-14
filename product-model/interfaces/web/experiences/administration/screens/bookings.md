---
entities:
- entity: booking
  shows:
  - Booker
  - Space
  - Enter
  - Leave
  - Subject
- entity: area
  shows:
  - Name
entryPoints:
- web: /ui/admin/bookings/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/bookings/index.tsx
- kind: code
  role: implementation
  target: server/service/booking-service.go#GetFiltered
---

# Bookings

The Organization's bookings for a chosen period, filtered by Area and by person, from which a bookings administrator opens, adds or deletes bookings and downloads the list.
