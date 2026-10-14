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
- text: The password is right and the User has neither an authenticator app nor a passkey
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Password
    - Authenticator app
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

# Sign in with a password

## Trigger

A User without a second factor opens Seatsurfing.

## Outcome

The User is signed in with a new session.
