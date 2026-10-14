---
availability:
- place: web::administration
domain: roles
references:
- kind: code
  role: implementation
  target: server/router/role-router.go#create
- kind: code
  role: implementation
  target: ui/src/pages/admin/roles/[id].tsx
---

# Create role

Define a Role with a name unique in the Organization and an access level per functionality, none above one's own.
