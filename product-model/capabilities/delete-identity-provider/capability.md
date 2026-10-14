---
availability:
- place: web::administration
domain: settings
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#delete
---

# Delete identity provider

Remove an identity provider and its mappings; providers managed outside the Organization stay.
