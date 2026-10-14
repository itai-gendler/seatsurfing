---
appliesTo:
- type: capability
  id: change-password
- type: capability
  id: reset-password
- type: capability
  id: accept-invitation
- type: capability
  id: create-user
references:
- kind: code
  role: implementation
  target: server/util/validation.go
---

# Passwords meet the password requirements

Every password a person or administrator sets is between 8 and 64 characters and meets the password requirements the sign-in pages show.
