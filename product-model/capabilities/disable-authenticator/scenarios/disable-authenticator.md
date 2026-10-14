---
kind: primary
routes:
  web: Web
steps:
- text: The User disables the authenticator app
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
- text: The Product forgets the User's authenticator
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

# Remove one's authenticator app

## Trigger

A User no longer wants an authenticator code at sign-in.

## Outcome

The User signs in without an authenticator code from now on.
