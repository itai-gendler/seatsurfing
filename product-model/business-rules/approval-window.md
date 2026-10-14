---
appliesTo:
- type: capability
  id: approve-booking
- type: capability
  id: decline-booking
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#approveBooking
- kind: code
  role: implementation
  target: server/repository/booking-repository.go#GetBookingsRequiringApproval
---

# A pending booking is decided until a day after it ends

A pending booking that ended more than 24 hours ago leaves the Approvals page and can no longer be approved or declined.
