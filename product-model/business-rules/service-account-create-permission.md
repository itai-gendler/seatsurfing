---
appliesTo:
- type: entity
  id: service-account
  effect: creates
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Users access
    is: Admin
  - entity: user
    fact: Service accounts access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#create
---

# Only administrators of both Users and service accounts create a service account

Creating a service account takes Users access Admin and Service accounts access Admin.
