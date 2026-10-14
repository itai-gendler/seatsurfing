---
entities:
- entity: user
  shows:
  - Email address
  - First name
  - Last name
  - Roles
- entity: service-account
  shows:
  - Name
  - Username
entryPoints:
- web: /ui/admin/users/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/users/index.tsx
---

# Users

The Organization's Users and service accounts, searchable, from which an administrator opens one or adds a new one.
