---
appliesTo:
- type: entity
  id: passkey
  effect: changes
  facts:
  - Name
permits:
- related:
  - verb: registers
    entity: user
references:
- kind: code
  role: implementation
  target: server/router/passkey-router.go#renamePasskey
---

# Only the person renames their own passkey

Renaming a passkey is the User's own.
