---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a person from the Users list
  kind: actor
  actor: user
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Email address
    - First name
    - Last name
  contexts:
    web:
      place: web::administration::users
- text: The User changes the names or email address and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product changes the person's details
  kind: product
  actor: user
  entities:
  - entity: user
    as: person
    effect: changes
    facts:
    - Email address
    - First name
    - Last name
  contexts:
    web:
      place: web::administration::user-editor
---

# Edit a user

## Trigger

A Users administrator corrects a person's details.

## Outcome

The User carries the new details.
