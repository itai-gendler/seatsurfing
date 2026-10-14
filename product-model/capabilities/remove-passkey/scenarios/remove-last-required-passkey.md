---
kind: validation
routes:
  web: Web
steps:
- text: The User removes their only passkey
  kind: actor
  actor: user
  entities:
  - entity: passkey
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Organization requires the User to have a second factor and the User has no authenticator app
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Enforce second factor
  - entity: user
    effect: reads
    facts:
    - Authenticator app
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product refuses to remove the passkey
  kind: product
  actor: user
  entities:
  - entity: passkey
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::preferences
---

# Last passkey kept while a second factor is required

## Trigger

A User whose Organization requires a second factor removes their only passkey and has no authenticator app.

## Outcome

The passkey stays.
