---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a name another Group already has and saves
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::group-editor
- text: The Product refuses the Group because the name already exists
  kind: product
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::group-editor
---

# Group name already taken

## Trigger

A Groups administrator names a new Group like an existing one.

## Outcome

No Group is created and the User is told the name already exists.
