---
actors:
- user
references:
- kind: code
  role: implementation
  target: ui/src/pages/_app.tsx
- kind: code
  role: implementation
  target: ui/src/components/TotpSetupModal.tsx
---

# Set up a required second factor

## Goal

A User whose Organization requires a second factor signs in and sets up an authenticator app before using Seatsurfing.

## Success criterion

The User is signed in and has an authenticator app.
