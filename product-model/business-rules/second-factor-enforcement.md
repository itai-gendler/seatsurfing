---
appliesTo:
- type: capability
  id: enable-authenticator
- type: capability
  id: remove-passkey
- type: capability
  id: sign-in
references:
- kind: code
  role: implementation
  target: server/router/routes.go#IsTotpEnforcedForUser
- kind: code
  role: implementation
  target: ui/src/pages/_app.tsx
- kind: spec
  role: intent
  target: specs/passkeys.md
---

# People the Organization requires to have a second factor set one up and keep one

While the Organization enforces a second factor for all users or for administrators, a covered person without an authenticator app or passkey is asked to set one up after signing in, and their last second factor stays. People signing in through an identity provider and service accounts are not covered.
