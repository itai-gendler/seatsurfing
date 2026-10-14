---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/space-router.go#delete
- kind: code
  role: implementation
  target: server/repository/space-repository.go#Delete
---

# Delete space

Remove a Space from its Area together with every booking and Recurring booking of it.
