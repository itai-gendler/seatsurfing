---
availability:
- place: web::administration
domain: settings
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#setMappings
---

# Remove provider mapping

Remove a mapping from an identity provider; at their next sign-in people lose what it alone granted.
