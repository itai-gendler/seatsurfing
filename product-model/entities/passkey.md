---
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/passkey-router.go
- kind: code
  role: implementation
  target: server/repository/passkey-repository.go
- kind: spec
  role: intent
  target: specs/passkeys.md
---

# Passkey

A passkey a User registered to sign in without a password, or as their second factor after the password.

## Information kept

- **Name** — the name the User gave it, such as the device
- **Key** — the credential held on the User's device; Seatsurfing keeps only what verifies it
- **Created** — when it was registered
- **Last used** — when it last signed the User in
