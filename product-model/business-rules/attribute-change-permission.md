---
appliesTo:
- type: entity
  id: attribute
  effect: changes
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Space attributes access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/space-attribute-router.go
---

# Only space attributes administrators change an attribute

Defining, changing and deleting attributes takes Space attributes access Admin.
