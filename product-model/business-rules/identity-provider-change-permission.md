---
appliesTo:
- type: entity
  id: identity-provider
  effect: changes
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Identity providers access
    is: Admin
  - fact: Managed
    is: 'No'
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#update
---

# Only identity providers administrators change a provider the Organization manages

Changing an identity provider takes Identity providers access Admin; providers managed outside the Organization are changed by nobody there.
