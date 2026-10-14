---
availability:
- place: web::administration
domain: settings
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#setMappings
---

# Add provider mapping

Add a mapping to an identity provider that reports groups: people whose provider groups include a value hold a Role or are members of a Group, refreshed at each sign-in. Nobody maps a Role granting more than they hold.
