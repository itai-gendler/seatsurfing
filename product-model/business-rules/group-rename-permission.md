---
appliesTo:
- type: entity
  id: group
  effect: changes
  facts:
  - Name
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
  target: server/router/group-router.go#update
---

# Only Groups administrators rename a Group

Renaming a Group takes Groups access Admin.
