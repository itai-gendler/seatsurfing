---
availability:
- place: web::administration
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#setRoles
---

# Remove user roles

Take Roles off a person in their user editor; Roles an identity provider assigns stay under the provider's control.
