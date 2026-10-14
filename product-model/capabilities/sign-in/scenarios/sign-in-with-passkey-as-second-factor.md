---
kind: primary
routes:
  web: Web
steps:
- text: The User enters their email address
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::public::sign-in
- text: The Product finds the Organization by the address and offers its sign-in methods
  kind: product
  actor: user
  entities:
  - entity: identity-provider
    effect: reads
    facts:
    - Name
  - entity: organization
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
- text: The User enters their password
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The password is right and the User has a passkey
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Password
  - entity: passkey
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
- text: The User confirms with their passkey
  kind: actor
  actor: user
  entities:
  - entity: passkey
    effect: reads
    facts: []
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

# Sign in with a password and a passkey

## Trigger

A User who registered a passkey signs in with their password.

## Outcome

The User is signed in after confirming with their passkey; one with an authenticator app may give its code instead.
