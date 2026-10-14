---
appliesTo:
- type: entity
  id: space
  effect: removes
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Areas access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/space-router.go#delete
---

# Only Areas administrators delete a Space

Deleting a Space, with everything booked in it, takes Areas access Admin.
