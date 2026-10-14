---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User enters the provider's endpoints, client credentials and user information fields, including the groups field, and saves
  kind: actor
  actor: user
  entities:
  - entity: identity-provider
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::identity-provider-editor
  capability: create-identity-provider
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
  capability: create-identity-provider
- text: The User adds a mapping from a group from provider to a Role or Group and saves
  kind: actor
  actor: user
  entities:
  - entity: provider-mapping
    effect: reads
    facts:
    - Group from provider
    - Target
  - entity: group
    effect: reads
    facts: []
  - entity: role
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::identity-provider-editor
  capability: add-provider-mapping
- text: The Product keeps the mapping
  kind: product
  actor: user
  entities:
  - entity: provider-mapping
    effect: creates
    facts:
    - Group from provider
    - Target
  - entity: identity-provider
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::identity-provider-editor
  capability: add-provider-mapping
---

# Create an identity provider and map its groups

## Trigger

An Organization moves its people to single sign-on.

## Outcome

People signing in through the provider receive the mapped Roles and Groups.
