---
availability:
- place: web::administration
- place: rest-api
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#delete
- kind: code
  role: implementation
  target: server/repository/user-repository.go#Delete
---

# Delete user

Remove a person or service account from the Organization together with their bookings, series, buddies, memberships and Roles. Nobody deletes their own account, and the Organization keeps at least one administrator.
