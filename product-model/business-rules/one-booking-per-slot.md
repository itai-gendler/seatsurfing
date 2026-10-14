---
appliesTo:
- type: capability
  id: book-space
- type: capability
  id: edit-booking
- type: capability
  id: request-public-booking
references:
- kind: code
  role: implementation
  target: server/repository/booking-repository.go#GetConflicts
---

# A Space holds at most one booking at any moment

No two bookings of a Space overlap, and a booking that waits for approval already holds its slot. Back-to-back bookings, one ending when the next starts, do not overlap.

## Rationale

Pending requests hold their slot so that an approver never confirms a booking another person took in the meantime.
