---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/space-router.go#removeApprovers
- kind: code
  role: implementation
  target: server/router/space-router.go#applyApprovers
---

# Remove space approvers

Take Groups off a Space's approver groups; with none left, new bookings of the Space need no approval.
