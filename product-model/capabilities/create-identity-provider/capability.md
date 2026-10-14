---
availability:
- place: web::administration
domain: settings
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#create
- kind: code
  role: implementation
  target: ui/src/pages/admin/settings/auth-providers/[id].tsx
---

# Create identity provider

Add an OAuth 2 or OpenID Connect provider the Organization's people sign in through, from a template or by hand. It exists while the Organization's plan includes identity providers.
