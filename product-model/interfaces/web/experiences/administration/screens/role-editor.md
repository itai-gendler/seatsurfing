---
entities:
- entity: role
  shows:
  - Name
  - Description
  - Access levels
  - Built-in
  collects:
  - Name
  - Description
  - Access levels
entryPoints:
- web: /ui/admin/roles/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/roles/[id].tsx
---

# Role editor

One Role with its name, description and, for each functionality, the access level it grants; the built-in Organization Administrator role is shown read-only.
