---
availability:
- place: web::booking-site
- place: web::public
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#setPassword
- kind: code
  role: implementation
  target: server/router/auth-router.go#updatePassword
- kind: code
  role: implementation
  target: ui/src/pages/preferences.tsx
---

# Change password

Choose a new password for one's own account, from Preferences, or at sign-in when an administrator set the current one. Changing it in Preferences signs the User out everywhere.
