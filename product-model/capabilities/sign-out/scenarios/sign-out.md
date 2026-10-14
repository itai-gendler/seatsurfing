---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Logout
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product ends the session
  kind: product
  actor: user
  entities:
  - entity: session
    effect: removes
  contexts:
    web:
      place: web::booking-site::book-a-space
---

# Sign out

## Trigger

A User leaves the Booking Site.

## Outcome

The User's session on this device is over.
