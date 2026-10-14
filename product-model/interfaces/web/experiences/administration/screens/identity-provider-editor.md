---
entities:
- entity: identity-provider
  shows:
  - Name
  - Endpoints
  - User information fields
  - Logout address
  - Profile page address
  - Managed
  collects:
  - Name
  - Endpoints
  - Client credentials
  - User information fields
  - Logout address
  - Profile page address
- entity: provider-mapping
  shows:
  - Group from provider
  - Target
  collects:
  - Group from provider
  - Target
- entity: role
  shows:
  - Name
- entity: group
  shows:
  - Name
entryPoints:
- web: /ui/admin/settings/auth-providers/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/settings/auth-providers/[id].tsx
---

# Identity provider editor

One identity provider with its endpoints, client credentials, user information fields and, once it exists and reports groups, its mappings to Roles and Groups.
