---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a person from the Users list
  kind: actor
  actor: user
  entities:
  - entity: user
    as: new-user
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::administration::users
- text: The User enters the email address, first and last name, chooses to send an invitation and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::administration::user-editor
- text: No User of the Organization has the address and the Organization is within its user limit
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Unlimited users feature
  - entity: user
    as: new-user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product creates the User with the invitation pending and emails the invitation link
  kind: product
  actor: user
  entities:
  - entity: user
    as: new-user
    effect: creates
    facts:
    - Email address
    - First name
    - Last name
    - Sign-in method
    - Identity provider
    - Password
    - Password change required
  contexts:
    web:
      place: web::administration::user-editor
---

# Invite a new user

## Trigger

A Users administrator adds a colleague who will choose their own password.

## Outcome

The User exists with an invitation pending, and receives an invitation email whose link is valid for three days.
