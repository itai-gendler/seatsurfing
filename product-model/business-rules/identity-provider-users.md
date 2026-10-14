---
appliesTo:
- type: capability
  id: sign-in
- type: capability
  id: reset-password
- type: capability
  id: add-passkey
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#callback
- kind: code
  role: implementation
  target: server/router/permissions.go#CanResetPassword
- kind: spec
  role: intent
  target: specs/passkeys.md
---

# People bound to an identity provider sign in only through it

A User bound to an identity provider signs in only through that provider; they have no password, password reset or passkeys in Seatsurfing.
