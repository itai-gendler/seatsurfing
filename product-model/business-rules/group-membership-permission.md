---
appliesTo:
- type: entity
  id: group
  effect: changes
  facts:
  - Members
  contexts:
  - place: web::administration::group-editor
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Groups access
    is: Write
- actors:
  - user
  when:
  - entity: user
    fact: Groups access
    is: Admin
references:
- kind: code
  role: implementation
  target: server/router/group-router.go#addMembers
- kind: code
  role: implementation
  target: server/router/group-router.go#removeMembers
---

# Groups access Write or Admin changes a Group's members

Adding and removing members in the group editor takes Groups access Write or Admin.
