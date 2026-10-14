---
availability:
- place: web::administration
domain: users
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#generateApiToken
- kind: spec
  role: intent
  target: specs/service-account-bearer-auth.md
---

# Generate API token

Give a service account a new long-lived API token, shown once, replacing any earlier one.
