---
kind: validation
routes:
  web: Web
steps:
- text: The User picks a level above their own for a functionality and saves
  kind: actor
  actor: user
  entities:
  - entity: role
    effect: reads
    facts:
    - Access levels
  contexts:
    web:
      place: web::administration::role-editor
- text: The Product refuses because the User cannot grant access they do not hold
  kind: product
  actor: user
  entities:
  - entity: role
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::role-editor
---

# Role beyond one's own access refused

## Trigger

A Roles administrator defines a Role granting more than they hold.

## Outcome

No Role is created.
