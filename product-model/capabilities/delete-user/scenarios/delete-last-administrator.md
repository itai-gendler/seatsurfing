---
kind: validation
routes:
  web: Web
steps:
- text: The User deletes the only remaining administrator
  kind: actor
  actor: user
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Email address
    - Roles
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product refuses because the Organization would be left without an administrator
  kind: product
  actor: user
  entities:
  - entity: role
    effect: reads
    facts:
    - Built-in
  - entity: organization
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
---

# Last administrator kept

## Trigger

A Users administrator deletes the only remaining holder of the Organization Administrator role.

## Outcome

Nothing is deleted and the User is told the Organization would be left without an administrator.
