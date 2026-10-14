---
availability:
- place: web::administration
domain: settings
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#update
---

# Edit identity provider

Change an identity provider's endpoints, credentials and fields; providers managed outside the Organization stay as they are.
