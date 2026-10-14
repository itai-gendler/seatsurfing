---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User enters their email address and the password they were given
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::public::sign-in
  capability: sign-in
- text: The Product finds the password must be changed and asks for a new one
  kind: product
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Password change required
  contexts:
    web:
      place: web::public::sign-in
  capability: sign-in
- text: The User enters the current and a new, different password
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::sign-in
  capability: change-password
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
  capability: change-password
---

# Sign in and choose one's own password

## Trigger

A User signs in for the first time with the password an administrator gave them.

## Outcome

The User has their own password and is signed in.
