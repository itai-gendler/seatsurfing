---
availability:
- place: web::administration
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#setRoles
- kind: code
  role: implementation
  target: server/router/permissions.go#CanGrantPermissions
---

# Add user roles

Give a person Roles in their user editor. Nobody changes their own Roles, and nobody hands out a Role granting more than they hold themselves.
