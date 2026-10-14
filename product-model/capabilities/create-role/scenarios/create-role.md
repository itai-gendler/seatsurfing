---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a Role from the Roles list
  kind: actor
  actor: user
  entities:
  - entity: role
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::roles
- text: The User enters a name and description, picks a level for each functionality and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::administration::role-editor
- text: The Product creates the Role
  kind: product
  actor: user
  entities:
  - entity: role
    effect: creates
    facts:
    - Name
    - Description
    - Access levels
    - Built-in
  contexts:
    web:
      place: web::administration::role-editor
---

# Create a role

## Trigger

A Roles administrator wants to grant part of the administration, such as Groups only.

## Outcome

The Role exists and can be given to people.

## Edge cases

- Functionalities offer only their meaningful levels, for example Areas only none or full access.
- A name another Role has is refused.
