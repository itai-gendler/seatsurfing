---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the email address, names and a starting password and saves
  kind: actor
  actor: user
  entities:
  - entity: user
    as: new-user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product creates the User, requiring a password change at first sign-in
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

# Create a user with a password

## Trigger

A Users administrator creates an account and hands over a starting password.

## Outcome

The User exists and must choose a new password at their first sign-in.
