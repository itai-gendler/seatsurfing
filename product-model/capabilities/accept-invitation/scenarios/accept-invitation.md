---
kind: primary
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
- text: The link is valid and no password is set yet
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Sign-in method
  contexts:
    web:
      place: web::public::accept-invitation
- text: The User enters a password meeting the requirements
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::accept-invitation
- text: The Product sets the password and makes password the User's sign-in method
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Password
    - Sign-in method
  contexts:
    web:
      place: web::public::accept-invitation
---

# Accept an invitation

## Trigger

An invited User opens the link from the invitation email.

## Outcome

The User has a password and can sign in.
