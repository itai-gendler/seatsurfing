---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a new password meeting the password requirements and saves
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product sets the new password and ends all the User's sessions
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
      place: web::booking-site::preferences
---

# Change one's password

## Trigger

A User wants a new password.

## Outcome

The new password is set, every session of the User ends and they sign in again.

## Edge cases

- People who sign in through an identity provider have no password here.
