---
availability:
- place: web::administration
- place: rest-api
domain: approvals
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#approveBooking
- kind: code
  role: implementation
  target: server/router/booking-router.go#onBookingDeclinedOrApproved
---

# Decline booking

An approver turns down a booking that waits for approval, from the Approvals page. The declined booking is removed and its slot freed; the same approvers who may approve a booking may decline it.
