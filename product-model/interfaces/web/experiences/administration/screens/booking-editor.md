---
entities:
- entity: booking
  shows:
  - Booker
  - Space
  - Enter
  - Leave
  - Subject
  - Public request
  collects:
  - Booker
  - Space
  - Enter
  - Leave
  - Subject
- entity: area
  shows:
  - Name
- entity: space
  shows:
  - Name
entryPoints:
- web: /ui/admin/bookings/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/bookings/[id].tsx
---

# Booking editor

One booking, or a new one, with the person it is for, the Area and Space, its times and subject.
