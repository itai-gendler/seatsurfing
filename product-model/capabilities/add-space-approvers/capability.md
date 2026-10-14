---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/space-router.go#addApprovers
- kind: code
  role: implementation
  target: server/router/space-router.go#applyApprovers
---

# Add space approvers

Name Groups as a Space's approver groups. While the Organization's plan includes Groups, new bookings of a Space with approver groups wait for approval by their members.
