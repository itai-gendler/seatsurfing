---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to sign in with a passkey and confirms on their device
  kind: actor
  actor: user
  entities:
  - entity: passkey
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
- text: The passkey belongs to an enabled User of the Organization
  kind: condition
  entities:
  - entity: passkey
    effect: reads
    facts: []
  - entity: organization
    effect: reads
    facts: []
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product records when the passkey was used
  kind: product
  actor: user
  entities:
  - entity: passkey
    effect: changes
    facts:
    - Last used
  contexts:
    web:
      place: web::public::sign-in
- text: The Product opens a session for the User and takes them to the Booking Site, or the administration when they came from there
  kind: product
  actor: user
  entities:
  - entity: session
    effect: creates
    facts:
    - Device
    - Created
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
---

# Sign in with a passkey alone

## Trigger

A User with a passkey signs in without typing a password.

## Outcome

The User is signed in.
