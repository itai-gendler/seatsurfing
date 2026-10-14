---
kind: primary
routes:
  web: Web
steps:
- text: The User reads their active sessions and signs one out, or all others
  kind: actor
  actor: user
  entities:
  - entity: session
    effect: reads
    facts:
    - Device
    - Created
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product ends those sessions
  kind: product
  actor: user
  entities:
  - entity: session
    effect: removes
  contexts:
    web:
      place: web::booking-site::preferences
---

# Sign out other devices

## Trigger

A User sees a session in their active sessions they want to end.

## Outcome

The chosen session, or every other session, is over.
