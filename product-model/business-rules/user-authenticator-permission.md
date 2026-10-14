---
appliesTo:
- type: entity
  id: user
  effect: changes
  facts:
  - Authenticator app
permits:
- self: true
- actors:
  - user
  when:
  - entity: user
    fact: Users access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#validateTotp
- kind: code
  role: implementation
  target: server/router/user-router.go#adminResetTotp
---

# A person manages their own authenticator app; Users administrators reset it

A User adds and removes their own authenticator app; a User with Users access Admin resets another person's.
