---
appliesTo:
- type: entity
  id: passkey
  effect: changes
  facts:
  - Last used
permits:
- related:
  - verb: registers
    entity: user
references:
- kind: code
  role: implementation
  target: server/router/passkey-router.go#finishPasskeyLogin
---

# A passkey records its own use

Signing in with a passkey records when it was last used, for the person it belongs to.
