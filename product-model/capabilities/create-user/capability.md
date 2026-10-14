---
availability:
- place: web::administration
- place: rest-api
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#create
- kind: code
  role: implementation
  target: ui/src/pages/admin/users/[id].tsx
---

# Create user

Add a person to the Organization, who sets their password from an invitation email, gets a password the administrator chose, or signs in through an identity provider; or add a service account for an integration. Without the unlimited users feature an Organization holds at most ten accounts.
