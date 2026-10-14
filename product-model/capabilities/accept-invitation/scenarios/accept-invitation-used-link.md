---
kind: edge
routes:
  web: Web
steps:
- text: The User opens the invitation link
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::accept-invitation
- text: A password was already set for the User
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Sign-in method
  contexts:
    web:
      place: web::public::accept-invitation
- text: The Product reports the link is no longer valid
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::accept-invitation
---

# Invitation link already used

## Trigger

An invited User opens the link after a password was already set.

## Outcome

Nothing changes and the User is told the link is no longer valid.
