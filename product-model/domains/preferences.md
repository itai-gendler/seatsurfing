---
references:
- kind: code
  role: implementation
  target: ui/src/pages/preferences.tsx
---

# Preferences

The Booking Site section where a User keeps their own preferences, password, authenticator app, passkeys and calendar connection.

## Boundary

Preferences owns a person's own settings and sign-in security. It does not own the Organization's settings, nor resets an administrator performs on someone else's account, which belong to Users.
