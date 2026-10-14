---
appliesTo:
- type: entity
  id: audit-entry
  effect: reads
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Audit log access
    is: Read
references:
- kind: code
  role: implementation
  target: server/router/auth-attempt-router.go
---

# Only audit log readers see the audit log

Reading sign-in attempts takes Audit log access Read.
