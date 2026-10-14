---
appliesTo:
- type: entity
  id: user
  effect: removes
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
  target: server/router/user-router.go#delete
---

# Only Users administrators delete a person

Deleting a person takes Users access Admin, for a User or a read-write service account.
