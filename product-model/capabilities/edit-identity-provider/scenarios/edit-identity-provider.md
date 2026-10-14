---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the provider's configuration and saves
  kind: actor
  actor: user
  entities:
  - entity: identity-provider
    effect: reads
    facts:
    - Name
    - Endpoints
    - User information fields
  contexts:
    web:
      place: web::administration::identity-provider-editor
- text: The Product changes the identity provider
  kind: product
  actor: user
  entities:
  - entity: identity-provider
    effect: changes
    facts:
    - Name
    - Endpoints
    - Client credentials
    - User information fields
    - Logout address
    - Profile page address
  contexts:
    web:
      place: web::administration::identity-provider-editor
---

# Edit an identity provider

## Trigger

A settings administrator updates the single sign-on configuration.

## Outcome

Sign-ins through the provider use the new configuration; the client secret stays unless a new one is entered.
