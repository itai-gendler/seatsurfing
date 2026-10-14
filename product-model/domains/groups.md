---
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/groups/index.tsx
---

# Groups

The administration section where Groups and their members are kept.

## Boundary

Groups owns creating, renaming and deleting Groups and their membership. It does not own where a Group is named as approver or allowed booker, which belongs to Areas, nor Roles and access levels.
