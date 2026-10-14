---
domain: settings
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#setMappings
- kind: code
  role: implementation
  target: server/router/permissions.go#ReconcileUserFromIdP
- kind: code
  role: implementation
  target: server/repository/auth-provider-mapping-repository.go
---

# Provider mapping

One rule of an identity provider: people whose provider groups include a value hold a Role or are members of a Group.

## Information kept

- **Group from provider** — the group value the provider reports
- **Target** — the Role or Group it grants
