---
kind: validation
routes:
  web: Web
steps:
- text: The User marks a Space as open to visitors and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: space
    effect: reads
    facts:
    - Public booking
    - Approver groups
  - entity: area
    effect: reads
    facts: []
  - entity: visitor
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Space has no approver groups
  kind: condition
  entities:
  - entity: space
    effect: reads
    facts:
    - Approver groups
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product refuses to save the Space
  kind: product
  actor: user
  entities:
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
---

# Public booking refused without approvers

## Trigger

An Areas administrator opens a Space with no approver groups to public booking.

## Outcome

The Space stays closed to public booking until it has at least one approver group.
