---
appliesTo:
- type: entity
  id: space
  effect: changes
  facts:
  - Attribute values
  contexts:
  - place: web::administration::attribute-editor
- type: entity
  id: area
  effect: changes
  facts:
  - Attribute values
  contexts:
  - place: web::administration::attribute-editor
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
  target: server/router/space-attribute-router.go#delete
---

# Deleting an attribute removes its values from Spaces and Areas

A User with Space attributes access Admin who deletes an attribute thereby removes every Space's and Area's value for it, without needing Areas access.
