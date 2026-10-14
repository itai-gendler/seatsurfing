---
appliesTo:
- type: entity
  id: area
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
  target: server/router/location-router.go#delete
---

# Only Areas administrators delete an Area

Deleting an Area, with everything booked in it, takes Areas access Admin.
