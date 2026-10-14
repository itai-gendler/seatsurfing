---
kind: edge
routes:
  web: Web
steps:
- text: The User enters an email address and asks for a reset link
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::reset-password
- text: No User with a password has that address
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::reset-password
- text: The Product confirms the request without sending anything
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::reset-password
---

# Reset asked for an unknown address

## Trigger

Someone asks for a reset link for an address with no password account.

## Outcome

No email is sent, and the page answers exactly as for a known address.
