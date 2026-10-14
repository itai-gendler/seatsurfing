---
appliesTo:
- type: entity
  id: group
  effect: removes
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Groups access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/group-router.go#delete
---

# Only Groups administrators delete a Group

Deleting a Group takes Groups access Admin.
