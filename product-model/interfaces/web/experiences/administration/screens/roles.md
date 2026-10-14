---
entities:
- entity: role
  shows:
  - Name
  - Description
  - Built-in
entryPoints:
- web: /ui/admin/roles/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/roles/index.tsx
---

# Roles

The Organization's Roles, from which an administrator opens one or adds a new one.
