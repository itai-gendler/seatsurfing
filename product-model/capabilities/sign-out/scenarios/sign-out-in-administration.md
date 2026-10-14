---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Logout in the administration
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::administration
- text: The Product ends the session
  kind: product
  actor: user
  entities:
  - entity: session
    effect: removes
  contexts:
    web:
      place: web::administration
---

# Sign out from the administration

## Trigger

A User leaves the administration.

## Outcome

The User's session on this device is over.
