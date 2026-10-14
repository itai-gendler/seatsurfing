---
entities:
- entity: user
  shows:
  - Email address
  collects:
  - Email address
  - Password
- entity: identity-provider
  shows:
  - Name
- entity: passkey
  collects:
  - Key
entryPoints:
- web: /ui/login/
references:
- kind: code
  role: implementation
  target: ui/src/pages/login/index.tsx
- kind: code
  role: implementation
  target: ui/src/pages/login/success/[id].tsx
---

# Sign in

Where a User signs in with email address and password, then an authenticator code or passkey where they have one, with a passkey alone, or through one of the Organization's identity providers; where a password change is required it is made here.
