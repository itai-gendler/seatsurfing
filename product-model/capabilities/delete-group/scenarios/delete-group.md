---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete in the group editor and confirms
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::group-editor
- text: The Product removes the Group
  kind: product
  actor: user
  entities:
  - entity: group
    effect: removes
  contexts:
    web:
      place: web::administration::group-editor
- text: The Product takes the Group off every Space's approver and allowed booker groups and every Area's allowed booker groups
  kind: product
  actor: user
  entities:
  - entity: space
    effect: changes
    facts:
    - Approver groups
    - Allowed booker groups
  - entity: area
    effect: changes
    facts:
    - Allowed booker groups
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::group-editor
---

# Delete a group

## Trigger

A Groups administrator no longer needs a Group.

## Outcome

The Group is gone; Spaces and Areas that named it lose it from their approver and allowed booker groups, so those left with none need no approval or are open to every User.
