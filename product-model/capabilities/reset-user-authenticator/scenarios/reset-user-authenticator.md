---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reset TOTP on a person and confirms
  kind: actor
  actor: user
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Authenticator app
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product forgets the person's authenticator
  kind: product
  actor: user
  entities:
  - entity: user
    as: person
    effect: changes
    facts:
    - Authenticator app
  contexts:
    web:
      place: web::administration::user-editor
---

# Reset a person's authenticator app

## Trigger

A person lost access to their authenticator app.

## Outcome

The person signs in without an authenticator code and may set up a new one.
