---
kind: validation
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
- text: The password or code is wrong, the account is disabled, or it is a service account
  kind: condition
  entities:
  - entity: user
    effect: reads
    facts:
    - Password
  - entity: service-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product refuses the sign-in
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::public::sign-in
---

# Sign-in refused

## Trigger

Someone enters a wrong password or code, or tries a disabled account.

## Outcome

Nobody is signed in and the attempt is refused without saying which part was wrong.
