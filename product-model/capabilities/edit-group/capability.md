---
availability:
- place: web::administration
domain: groups
references:
- kind: code
  role: implementation
  target: server/router/group-router.go#update
---

# Edit group

Rename a Group, keeping its name unique in the Organization.
