---
references:
- kind: code
  role: implementation
  target: server/router/auth-attempt-router.go
- kind: code
  role: implementation
  target: server/repository/auth-attempt-repository.go
---

# Audit entry

One sign-in attempt in the Organization's audit log: who tried, how, from which device, when and with which outcome.

## Information kept

- **Time** — when the attempt happened
- **Email address** — the address that was used
- **Method** — password, authenticator code, passkey or identity provider
- **Outcome** — Successful or Failed, with the reason for a failure
- **Device** — the browser and operating system
- **Identity provider** — the provider used, if any
