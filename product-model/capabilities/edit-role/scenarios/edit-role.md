---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the Role's name, description or levels and saves
  kind: actor
  actor: user
  entities:
  - entity: role
    effect: reads
    facts:
    - Name
    - Description
    - Access levels
  contexts:
    web:
      place: web::administration::role-editor
- text: The Role is not built in and the User holds every level it grants before and after
  kind: condition
  entities:
  - entity: role
    effect: reads
    facts:
    - Built-in
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::role-editor
- text: The Product changes the Role
  kind: product
  actor: user
  entities:
  - entity: role
    effect: changes
    facts:
    - Name
    - Description
    - Access levels
  contexts:
    web:
      place: web::administration::role-editor
---

# Edit a role

## Trigger

A Roles administrator changes what a Role grants.

## Outcome

Everyone holding the Role has its new access.
