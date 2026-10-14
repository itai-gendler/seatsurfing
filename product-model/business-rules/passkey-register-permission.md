---
appliesTo:
- type: entity
  id: passkey
  effect: creates
permits:
- related:
  - verb: registers
    entity: user
references:
- kind: code
  role: implementation
  target: server/router/passkey-router.go#beginPasskeyRegistration
---

# Only the person registers or renames their own passkeys

Registering and renaming a passkey is the User's own, from the Organization's primary address.
