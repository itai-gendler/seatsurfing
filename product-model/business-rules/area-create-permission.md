---
appliesTo:
- type: entity
  id: area
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
  target: server/router/location-router.go#create
---

# Only Areas administrators create an Area

Creating an Area takes Areas access Admin.
