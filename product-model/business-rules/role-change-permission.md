---
appliesTo:
- type: entity
  id: role
  effect: changes
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Roles access
    is: Admin
  - fact: Built-in
    is: 'No'
references:
- kind: code
  role: implementation
  target: server/router/role-router.go
---

# Only Roles administrators change a Role, and never the built-in one

Changing a Role takes Roles access Admin; the built-in Organization Administrator role is changed by nobody.
