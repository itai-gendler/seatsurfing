---
appliesTo:
- type: capability
  id: sign-in
- type: entity
  id: audit-entry
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#recordAuthEvent
- kind: code
  role: implementation
  target: server/repository/auth-attempt-repository.go
---

# Every sign-in attempt is recorded in the audit log

Each attempt to sign in, successful or not, becomes an audit entry with who tried, how, from which device and with which outcome.
