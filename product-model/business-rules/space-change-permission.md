---
appliesTo:
- type: entity
  id: space
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
  target: server/router/space-router.go#update
---

# Only Areas administrators change a Space in the area editor

Changing a Space's settings, floor plan, approver groups or allowed booker groups takes Areas access Admin.
