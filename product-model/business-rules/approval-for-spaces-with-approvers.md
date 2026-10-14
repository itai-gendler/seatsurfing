---
appliesTo:
- type: capability
  id: book-space
- type: capability
  id: request-public-booking
references:
- kind: code
  role: implementation
  target: server/service/space-service.go#RequiresApproval
- kind: code
  role: implementation
  target: server/service/booking-service.go#CommitCreate
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#confirm
---

# New bookings of a Space with approver groups wait for approval

While the Organization's plan includes Groups, a booking of a Space with at least one approver group starts waiting for approval, and every public request starts waiting for approval. Other bookings are confirmed at once.
