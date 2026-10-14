---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on the Role and confirms
  kind: actor
  actor: user
  entities:
  - entity: role
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::role-editor
- text: The Role is not built in and the User holds every level it grants
  kind: condition
  entities:
  - entity: role
    effect: reads
    facts:
    - Built-in
    - Access levels
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::role-editor
- text: The Product removes the Role
  kind: product
  actor: user
  entities:
  - entity: role
    effect: removes
  contexts:
    web:
      place: web::administration::role-editor
---

# Delete a role

## Trigger

A Roles administrator no longer needs a Role.

## Outcome

The Role is gone and its holders lose what only it granted.
