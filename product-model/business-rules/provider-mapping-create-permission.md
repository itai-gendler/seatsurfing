---
appliesTo:
- type: entity
  id: provider-mapping
  effect: creates
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Identity providers access
    is: Admin
  - entity: user
    fact: Roles access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#setMappings
---

# Only administrators of both identity providers and Roles add a provider mapping

Adding a mapping takes Identity providers access Admin and Roles access Admin.
