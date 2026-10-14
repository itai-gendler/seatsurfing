---
entities:
- entity: user
  shows:
  - Email address
  - First name
  - Last name
  - Sign-in method
  - Identity provider
  - Roles
  - Authenticator app
  - Has passkeys
  collects:
  - Email address
  - First name
  - Last name
  - Sign-in method
  - Identity provider
  - Password
  - Roles
- entity: service-account
  shows:
  - Name
  - Username
  - Access mode
  - API token
  collects:
  - Name
  - Username
  - Access mode
  - Password
- entity: role
  shows:
  - Name
- entity: identity-provider
  shows:
  - Name
entryPoints:
- web: /ui/admin/users/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/users/[id].tsx
---

# User editor

One User or service account: names, email address or username, kind of account, sign-in method, Roles, second factors and, for a service account, its API token.
