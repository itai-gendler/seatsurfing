---
appliesTo:
- type: entity
  id: area
  effect: changes
  contexts:
  - place: web::administration::area-editor
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
  target: server/router/location-router.go#update
---

# Only Areas administrators change an Area in the area editor

Changing an Area's settings, floor plan or allowed booker groups takes Areas access Admin.
