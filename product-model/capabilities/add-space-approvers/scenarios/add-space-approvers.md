---
kind: primary
routes:
  web: Web
steps:
- text: The User adds Groups to the Space's approvers and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  - entity: area
    effect: reads
    facts: []
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product adds the Groups to the Space's approver groups
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

# Require approval for a space

## Trigger

An Areas administrator wants bookings of a Space approved before they count.

## Outcome

New bookings of the Space wait for approval by members of its approver groups; existing bookings keep their state.
