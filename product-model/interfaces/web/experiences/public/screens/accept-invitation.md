---
entities:
- entity: user
  collects:
  - Password
entryPoints:
- web: /ui/setpw/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/setpw/[id].tsx
---

# Accept invitation

Where an invited User, coming from the invitation email, chooses their password.
