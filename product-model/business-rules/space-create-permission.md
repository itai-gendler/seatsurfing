---
appliesTo:
- type: entity
  id: space
  effect: creates
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
  target: server/router/space-router.go#create
---

# Only Areas administrators create a Space

Creating a Space takes Areas access Admin.
