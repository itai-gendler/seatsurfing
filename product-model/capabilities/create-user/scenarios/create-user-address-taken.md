---
kind: validation
routes:
  web: Web
steps:
- text: The User enters an address another User has and saves
  kind: actor
  actor: user
  entities:
  - entity: user
    as: new-user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product refuses because the user already exists
  kind: product
  actor: user
  entities:
  - entity: user
    as: new-user
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::administration::user-editor
---

# Address already taken

## Trigger

A Users administrator adds a person whose address another User of the Organization has.

## Outcome

No User is created and the User is told the user already exists.

## Edge cases

- An Organization at its limit of ten accounts refuses new ones until its plan includes unlimited users.
