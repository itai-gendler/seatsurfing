---
entities:
- entity: group
  shows:
  - Name
  - Members
  collects:
  - Name
  - Members
- entity: user
  shows:
  - Email address
  - First name
  - Last name
entryPoints:
- web: /ui/admin/groups/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/groups/[id].tsx
---

# Group editor

One Group with its name and, once it exists, its members.
