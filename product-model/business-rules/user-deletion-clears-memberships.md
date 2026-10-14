---
appliesTo:
- type: entity
  id: group
  effect: changes
  facts:
  - Members
  contexts:
  - place: web::administration::user-editor
  - place: rest-api
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Users access
    is: Admin
- actors:
  - service-account
  when:
  - entity: service-account
    fact: Users access
    is: Admin
  - entity: service-account
    fact: Access mode
    is: Read-write
references:
- kind: code
  role: implementation
  target: server/repository/user-repository.go#Delete
---

# Deleting a person takes them out of their Groups

Whoever may delete a person thereby takes them out of every Group, without needing Groups access.
