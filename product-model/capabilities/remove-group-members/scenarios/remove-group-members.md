---
kind: primary
routes:
  web: Web
steps:
- text: The User selects members of the Group and removes them
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Members
  - entity: user
    as: member
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::administration::group-editor
- text: The Product removes the Users from the Group's members
  kind: product
  actor: user
  entities:
  - entity: group
    effect: changes
    facts:
    - Members
  - entity: user
    as: member
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::group-editor
---

# Remove members from a group

## Trigger

A User who manages Group membership takes people out of a Group.

## Outcome

The Users are no longer members and lose what the Group allowed them to book or approve.
