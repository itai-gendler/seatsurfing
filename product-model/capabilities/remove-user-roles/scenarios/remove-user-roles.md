---
kind: primary
routes:
  web: Web
steps:
- text: The User removes Roles from a person and saves
  kind: actor
  actor: user
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Roles
  - entity: role
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: Another administrator remains, the User holds every level the Roles grant and is not editing their own account
  kind: condition
  entities:
  - entity: role
    effect: reads
    facts:
    - Access levels
    - Built-in
  - entity: user
    as: person
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product takes the Roles off the person
  kind: product
  actor: user
  entities:
  - entity: user
    as: person
    effect: changes
    facts:
    - Roles
  - entity: role
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
---

# Take roles off a person

## Trigger

A person no longer needs administrative access.

## Outcome

The person no longer holds the Roles and loses what only they granted.
