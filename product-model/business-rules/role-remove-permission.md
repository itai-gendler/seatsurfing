---
appliesTo:
- type: entity
  id: role
  effect: removes
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

# Only Roles administrators delete a Role, and never the built-in one

Deleting a Role takes Roles access Admin; the built-in Organization Administrator role is deleted by nobody.
