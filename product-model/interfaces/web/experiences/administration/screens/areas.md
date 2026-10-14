---
entities:
- entity: area
  shows:
  - Name
  - Enabled
entryPoints:
- web: /ui/admin/locations/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/locations/index.tsx
---

# Areas

The list of the Organization's Areas, from which an administrator opens one, adds a new one or goes to the attributes.
