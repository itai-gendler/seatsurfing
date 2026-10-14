---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on the provider and confirms
  kind: actor
  actor: user
  entities:
  - entity: identity-provider
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::identity-provider-editor
- text: The Product removes the identity provider with its mappings
  kind: product
  actor: user
  entities:
  - entity: identity-provider
    effect: removes
  - entity: provider-mapping
    effect: removes
    with: identity-provider
  contexts:
    web:
      place: web::administration::identity-provider-editor
---

# Delete an identity provider

## Trigger

The Organization stops using a provider.

## Outcome

The provider is no longer offered at sign-in and its mappings are gone.
