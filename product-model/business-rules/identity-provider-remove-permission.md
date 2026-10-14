---
appliesTo:
- type: entity
  id: identity-provider
  effect: removes
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
  target: server/router/auth-provider-router.go#delete
---

# Only identity providers administrators delete a provider the Organization manages

Deleting an identity provider takes Identity providers access Admin; providers managed outside the Organization are deleted by nobody there.
