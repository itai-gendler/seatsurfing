---
kind: validation
routes:
  web: Web
steps:
- text: The User adds a Role granting a level they do not hold and saves
  kind: actor
  actor: user
  entities:
  - entity: role
    effect: reads
    facts:
    - Name
  - entity: user
    as: person
    effect: reads
    facts:
    - Roles
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product refuses the change
  kind: product
  actor: user
  entities:
  - entity: role
    effect: reads
    facts:
    - Access levels
  contexts:
    web:
      place: web::administration::user-editor
---

# Role beyond one's own access refused

## Trigger

A Roles administrator tries to give a Role granting more than they hold.

## Outcome

Nothing changes and the User is told they cannot grant access they do not hold.
