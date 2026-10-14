---
kind: validation
routes:
  web: Web
steps:
- text: The User removes every approver group of a Space open to visitors and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: space
    effect: reads
    facts:
    - Approver groups
    - Public booking
  - entity: area
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  - entity: visitor
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product refuses the change
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

# Last approver of a public space kept

## Trigger

An Areas administrator removes every approver group of a Space open to public booking.

## Outcome

The Space keeps its approver groups; it must be closed to public booking first.
