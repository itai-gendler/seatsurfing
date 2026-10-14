---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User signs in with email address and password
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
  capability: sign-in
- text: The Product opens a session and, because the Organization requires a second factor, asks the User to set one up before going on
  kind: product
  actor: user
  entities:
  - entity: session
    effect: creates
    facts:
    - Device
    - Created
  - entity: organization
    effect: reads
    facts:
    - Enforce second factor
  contexts:
    web:
      place: web::public::sign-in
  capability: sign-in
- text: The User scans the code and enters the six-digit code the app shows
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::preferences
  capability: enable-authenticator
- text: The Product checks the code and keeps the authenticator for the User
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Authenticator app
  contexts:
    web:
      place: web::booking-site::preferences
  capability: enable-authenticator
---

# Sign in and set up the required authenticator app

## Trigger

A User without a second factor signs in to an Organization that enforces one.

## Outcome

The User has an authenticator app and uses the Booking Site.
