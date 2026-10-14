---
appliesTo:
- type: entity
  id: passkey
  effect: removes
permits:
- related:
  - verb: registers
    entity: user
- actors:
  - user
  when:
  - entity: user
    fact: Users access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/passkey-router.go#deletePasskey
- kind: code
  role: implementation
  target: server/router/user-router.go#adminResetPasskeys
---

# Only the person registers, renames and removes their passkeys; Users administrators reset them

A User registers, renames and removes their own passkeys; a User with Users access Admin removes all of another person's.
