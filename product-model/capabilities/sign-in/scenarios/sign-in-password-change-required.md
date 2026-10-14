---
kind: primary
routes:
  web: Web
steps:
- text: The User enters their email address
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
- text: The Product finds the Organization by the address and offers its sign-in methods
  kind: product
  actor: user
  entities:
  - entity: identity-provider
    effect: reads
    facts:
    - Name
  - entity: organization
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
- text: The User enters their password
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The password is right and its change is required
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Password
    - Password change required
  contexts:
    web:
      place: web::public::sign-in
- text: The Product asks the User to choose a new password
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::sign-in
---

# Sign-in asks for a new password

## Trigger

A User signs in with a password an administrator set.

## Outcome

The User is asked to choose their own password before the session opens.
