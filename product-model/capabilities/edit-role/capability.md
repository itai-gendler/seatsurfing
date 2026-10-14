---
availability:
- place: web::administration
domain: roles
references:
- kind: code
  role: implementation
  target: server/router/role-router.go#update
---

# Edit role

Change a Role's name, description and levels; the built-in Organization Administrator role never changes.
