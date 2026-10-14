---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a passkey and names it
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
- text: The Product asks the device to create the passkey
  kind: product
  actor: user
  entities:
  - entity: passkey
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::preferences
- text: The User confirms on their device
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product keeps the passkey for the User
  kind: product
  actor: user
  entities:
  - entity: passkey
    effect: creates
    facts:
    - Name
    - Created
  contexts:
    web:
      place: web::booking-site::preferences
---

# Register a passkey

## Trigger

A User wants to sign in with a passkey.

## Outcome

The passkey is listed under the name the User gave and signs them in from now on.

## Edge cases

- Each User holds a limited number of passkeys set by the installation, ten unless configured otherwise.
