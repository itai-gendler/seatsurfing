---
appliesTo:
- type: entity
  id: space
  effect: changes
  facts:
  - Approver groups
  - Allowed booker groups
  contexts:
  - place: web::administration::group-editor
- type: entity
  id: area
  effect: changes
  facts:
  - Allowed booker groups
  contexts:
  - place: web::administration::group-editor
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
  target: server/repository/group-repository.go#Delete
---

# Deleting a Group takes it off every Space's and Area's lists

A User with Groups access Admin who deletes a Group thereby removes it from every Space's approver and allowed booker groups and every Area's allowed booker groups, without needing Areas access.
