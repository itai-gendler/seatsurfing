---
entities:
- entity: area
  shows:
  - Name
  - Floor plan
- entity: space
  shows:
  - Name
  - Position on floor plan
  - Subject required
  - Attribute values
- entity: booking
  shows:
  - Enter
  - Leave
  - Subject
  - Booker
  collects:
  - Space
  - Enter
  - Leave
  - Subject
- entity: recurring-booking
  collects:
  - Cadence
  - Cycle
  - Weekdays
  - End date
- entity: buddy
  shows:
  - Colleague
entryPoints:
- web: /ui/search/
references:
- kind: code
  role: implementation
  target: ui/src/pages/search.tsx
- kind: code
  role: implementation
  target: server/router/space-router.go#_getAvailability
---

# Book a space

The Booking Site's main page: the User picks an Area, a day and a time slot, filters by attributes or buddies, sees on the floor plan which Spaces are free, booked, booked by them or a buddy, or not allowed, and which need approval, and books a Space once or as a recurring series.
