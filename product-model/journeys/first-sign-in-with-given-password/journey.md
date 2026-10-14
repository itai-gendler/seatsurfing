---
actors:
- user
references:
- kind: code
  role: implementation
  target: ui/src/pages/login/index.tsx
- kind: code
  role: implementation
  target: server/router/auth-router.go#updatePassword
---

# First sign-in with a given password

## Goal

A User whose administrator set their password signs in and replaces it with their own.

## Success criterion

The User is signed in with a password of their own.
