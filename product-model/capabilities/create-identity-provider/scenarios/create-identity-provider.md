---
kind: primary
routes:
  web: Web
steps:
- text: The User adds an identity provider from the settings
  kind: actor
  actor: user
  entities:
  - entity: identity-provider
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::settings
- text: The User picks a template or enters the endpoints, client credentials and user information fields and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::administration::identity-provider-editor
- text: The Product creates the identity provider and opens it in its editor
  kind: product
  actor: user
  entities:
  - entity: identity-provider
    effect: creates
    facts:
    - Name
    - Endpoints
    - Client credentials
    - User information fields
    - Logout address
    - Profile page address
    - Managed
  contexts:
    web:
      place: web::administration::identity-provider-editor
---

# Create an identity provider

## Trigger

A settings administrator connects the Organization's single sign-on.

## Outcome

The provider is offered on the sign-in page and opens in its editor, where mappings can be added once it reports groups.

## Edge cases

- A name another identity provider of the Organization has is refused.
