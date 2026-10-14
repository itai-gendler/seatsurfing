---
kind: primary
routes:
  web: Web
steps:
- text: The User adds Roles to a person and saves
  kind: actor
  actor: user
  entities:
  - entity: role
    effect: reads
    facts:
    - Name
  - entity: user
    as: person
    effect: reads
    facts:
    - Roles
  contexts:
    web:
      place: web::administration::user-editor
- text: The User holds at least every level the Roles grant and is not editing their own account
  kind: condition
  entities:
  - entity: role
    effect: reads
    facts:
    - Access levels
  - entity: user
    as: person
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product assigns the Roles to the person
  kind: product
  actor: user
  entities:
  - entity: user
    as: person
    effect: changes
    facts:
    - Roles
  - entity: role
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
---

# Give a person roles

## Trigger

A Roles administrator lets a person administer part of the Organization.

## Outcome

The person holds the Roles and their access is the highest level any of their Roles grants.
