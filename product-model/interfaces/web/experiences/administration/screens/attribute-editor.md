---
entities:
- entity: attribute
  shows:
  - Label
  - Type
  - Applies to spaces
  - Applies to areas
  collects:
  - Label
  - Type
  - Applies to spaces
  - Applies to areas
entryPoints:
- web: /ui/admin/attributes/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/attributes/[id].tsx
---

# Attribute editor

One attribute with its label, type and whether it applies to Spaces, Areas or both.
