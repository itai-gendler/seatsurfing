---
appliesTo:
- type: entity
  id: identity-provider
  effect: creates
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Identity providers access
    is: Admin
  - entity: organization
    fact: Identity providers feature
    is: 'On'
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go#create
---

# Only identity providers administrators add one, while the plan includes identity providers

Adding an identity provider takes Identity providers access Admin and an Organization whose plan includes identity providers.
