---
kind: primary
routes:
  web: Web
steps:
- text: The User starts the authenticator setup
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Authenticator app
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product shows a code to scan, valid for five minutes
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::preferences
- text: The User scans it and enters the six-digit code the app shows
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::preferences
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
---

# Set up an authenticator app

## Trigger

A User wants a second factor for their password.

## Outcome

The authenticator app gives the User's second factor from the next sign-in on.
