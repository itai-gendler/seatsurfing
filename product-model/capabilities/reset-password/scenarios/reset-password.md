---
kind: primary
routes:
  web: Web
steps:
- text: The User enters their email address and asks for a reset link
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::reset-password
- text: The Product emails the User a link valid for one hour
  kind: product
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::public::reset-password
- text: The User opens the link and enters a new password meeting the requirements
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::reset-password
- text: The Product sets the new password and ends the User's sessions
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Password
  - entity: session
    effect: removes
  contexts:
    web:
      place: web::public::reset-password
---

# Reset a forgotten password

## Trigger

A User forgot their password.

## Outcome

The User has a new password and every earlier session of theirs is over.
