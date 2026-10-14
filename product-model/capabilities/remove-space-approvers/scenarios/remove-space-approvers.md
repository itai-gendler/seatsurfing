---
kind: primary
routes:
  web: Web
steps:
- text: The User removes Groups from the Space's approvers and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: space
    effect: reads
    facts:
    - Approver groups
  - entity: area
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product removes the Groups from the Space's approver groups
  kind: product
  actor: user
  entities:
  - entity: space
    effect: changes
    facts:
    - Approver groups
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
---

# Remove approvers from a space

## Trigger

An Areas administrator changes who approves a Space's bookings.

## Outcome

The removed Groups no longer approve the Space; with none left, new bookings are confirmed at once while bookings already pending still wait.
