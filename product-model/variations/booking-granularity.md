---
kind: configuration
of: capability-scenario
settings:
- entity: organization
  fact: Daily basis booking
takesEffect: When a User books. A settings change applies to the next booking.
stability: Existing bookings keep their times when the setting changes.
alternatives:
- id: book-space-for-time-slot
  selectedWhen: Daily basis booking is off. A missing setting counts as off.
- id: book-space-for-whole-days
  selectedWhen: Daily basis booking is on.
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#IsValidBookingDuration
- kind: code
  role: implementation
  target: ui/src/pages/search.tsx
---

# Booking granularity

Organizations book either by time slot within a day or by whole days; both ways of booking are supported.
