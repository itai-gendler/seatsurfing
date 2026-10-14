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
  target: server/service/booking-service.go#CanApproveBookingsInSpace
- kind: code
  role: implementation
  target: ui/src/pages/admin/approvals/index.tsx
---

# Approve booking

An approver confirms a booking that waits for approval, from the Approvals page. Approvers with Approvals access Write decide the bookings of Spaces whose approver groups include them; Approvals access Admin decides every pending booking of the Organization.
