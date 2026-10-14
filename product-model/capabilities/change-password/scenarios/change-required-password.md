---
kind: primary
routes:
  web: Web
steps:
- text: The User's password change is required
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Password change required
  contexts:
    web:
      place: web::public::sign-in
- text: The User enters the current and a new, different password
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product sets the new password, clears the requirement and signs the User in
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Password
    - Password change required
  - entity: session
    effect: creates
    facts:
    - Device
    - Created
  contexts:
    web:
      place: web::public::sign-in
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#updatePassword
---

# Choose a new password at sign-in

## Trigger

A User signs in with a password an administrator set, which must be changed.

## Outcome

The User has their own password and is signed in.
