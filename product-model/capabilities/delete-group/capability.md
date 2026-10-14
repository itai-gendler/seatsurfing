---
availability:
- place: web::administration
domain: groups
references:
- kind: code
  role: implementation
  target: server/router/group-router.go#delete
- kind: code
  role: implementation
  target: server/repository/group-repository.go#Delete
---

# Delete group

Remove a Group; it also stops being an approver group or allowed booker group of every Space and Area.
