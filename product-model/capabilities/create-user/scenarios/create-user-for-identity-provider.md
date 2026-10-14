---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the email address and names, chooses an identity provider and saves
  kind: actor
  actor: user
  entities:
  - entity: identity-provider
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product creates the User bound to the identity provider
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
  - entity: identity-provider
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::user-editor
---

# Create a user who signs in through an identity provider

## Trigger

A Users administrator adds a person who signs in through the Organization's identity provider.

## Outcome

The User exists bound to that provider and signs in only through it.
