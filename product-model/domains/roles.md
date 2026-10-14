---
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/roles/index.tsx
---

# Roles

The administration section where the Organization defines Roles and the access levels they grant.

## Boundary

Roles owns defining Roles. It does not own assigning them to people, which belongs to Users, nor identity provider mappings, which belong to Settings.
