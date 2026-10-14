---
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/settings/index.tsx
---

# Settings

The administration section holding the Organization's settings and its identity providers with their mappings.

## Boundary

Settings owns the Organization's settings and identity providers. It does not own the plan features, which only show there, nor the Roles and Groups mappings point at.
