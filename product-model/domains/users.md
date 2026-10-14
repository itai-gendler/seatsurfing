---
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/users/index.tsx
---

# Users

The administration section where the Organization's Users and service accounts are created, changed and deleted, given Roles, and have their second factors and API tokens reset.

## Boundary

Users owns accounts and which Roles they hold. It does not own what a Role grants, which belongs to Roles, nor a person's own preferences and security settings.
