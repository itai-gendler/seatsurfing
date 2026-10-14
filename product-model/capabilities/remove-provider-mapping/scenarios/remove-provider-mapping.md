---
kind: primary
routes:
  web: Web
steps:
- text: The User removes a mapping and saves the provider
  kind: actor
  actor: user
  entities:
  - entity: provider-mapping
    effect: reads
    facts:
    - Group from provider
    - Target
  contexts:
    web:
      place: web::administration::identity-provider-editor
- text: The Product removes the mapping
  kind: product
  actor: user
  entities:
  - entity: provider-mapping
    effect: removes
  - entity: identity-provider
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::identity-provider-editor
---

# Remove a provider mapping

## Trigger

A provider group should no longer grant a Role or Group.

## Outcome

At their next sign-in, people lose the Role or Group membership the mapping granted.
