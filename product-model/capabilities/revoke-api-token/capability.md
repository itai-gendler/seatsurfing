---
availability:
- place: web::administration
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#revokeApiToken
---

# Revoke API token

Remove a service account's API token so it no longer authenticates with it.
