---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a code that does not match
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
- text: The Product refuses the code
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::preferences
---

# Authenticator code not accepted

## Trigger

The code a User enters during setup does not match.

## Outcome

No authenticator is kept; the User may try again a few times before starting over.
