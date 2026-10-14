---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to resend the invitation and saves
  kind: actor
  actor: user
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Sign-in method
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product resets the person's sign-in to a pending invitation, ends their sessions and emails a new link
  kind: product
  actor: user
  entities:
  - entity: user
    as: person
    effect: changes
    facts:
    - Sign-in method
    - Password
    - Identity provider
  - entity: session
    effect: removes
  contexts:
    web:
      place: web::administration::user-editor
---

# Send a new invitation

## Trigger

A person lost their invitation or should set a new password themselves.

## Outcome

The person's sign-in is reset to a pending invitation, their sessions end and a new invitation email goes out.
