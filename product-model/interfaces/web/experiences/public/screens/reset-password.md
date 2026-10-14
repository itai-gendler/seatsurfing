---
entities:
- entity: user
  collects:
  - Email address
  - Password
entryPoints:
- web: /ui/resetpw/
references:
- kind: code
  role: implementation
  target: ui/src/pages/resetpw/index.tsx
- kind: code
  role: implementation
  target: ui/src/pages/resetpw/[id].tsx
---

# Reset password

Where a User asks for a password reset link and, coming back from it, chooses a new password.
