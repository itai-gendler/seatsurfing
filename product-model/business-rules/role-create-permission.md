---
appliesTo:
- type: entity
  id: role
  effect: creates
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Roles access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/role-router.go
---

# Only Roles administrators create a Role

Creating a Role takes Roles access Admin.
