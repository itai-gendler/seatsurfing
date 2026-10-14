---
appliesTo:
- type: entity
  id: service-account
  effect: changes
  facts:
  - API token
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Service accounts access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#generateApiToken
- kind: code
  role: implementation
  target: server/router/user-router.go#revokeApiToken
---

# Only service accounts administrators generate and revoke API tokens

Generating or revoking a service account's API token takes Service accounts access Admin.
