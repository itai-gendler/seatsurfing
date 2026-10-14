---
availability:
- place: web::administration
domain: roles
references:
- kind: code
  role: implementation
  target: server/router/role-router.go#delete
---

# Delete role

Remove a Role from the Organization and from everyone holding it; the built-in Organization Administrator role stays.
