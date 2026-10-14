---
kind: primary
routes:
  web: Web
steps:
- text: The User removes one of their passkeys and confirms
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
- text: The Product forgets the passkey
  kind: product
  actor: user
  entities:
  - entity: passkey
    effect: removes
  contexts:
    web:
      place: web::booking-site::preferences
---

# Remove a passkey

## Trigger

A User no longer uses a passkey.

## Outcome

The passkey no longer signs the User in.
