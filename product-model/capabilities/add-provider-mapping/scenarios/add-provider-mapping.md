---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a mapping from a group from provider to a Role or Group and saves the provider
  kind: actor
  actor: user
  entities:
  - entity: provider-mapping
    effect: reads
    facts:
    - Group from provider
    - Target
  - entity: role
    effect: reads
    facts:
    - Name
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::identity-provider-editor
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
---

# Map a provider group to a role or group

## Trigger

A settings administrator lets the identity provider decide part of people's access.

## Outcome

From their next sign-in, people in that provider group hold the Role or are members of the Group.
