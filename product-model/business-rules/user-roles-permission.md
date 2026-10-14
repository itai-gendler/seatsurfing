---
appliesTo:
- type: entity
  id: user
  effect: changes
  facts:
  - Roles
  contexts:
  - place: web::administration::user-editor
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
  target: server/router/user-router.go#setRoles
---

# Only Roles administrators change which Roles a person holds

Adding or removing a person's Roles in the user editor takes Roles access Admin.
