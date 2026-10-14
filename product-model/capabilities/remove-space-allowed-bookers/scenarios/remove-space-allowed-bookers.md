---
kind: primary
routes:
  web: Web
steps:
- text: The User removes Groups from the Space's allowed bookers and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: space
    effect: reads
    facts:
    - Allowed booker groups
  - entity: area
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product removes the Groups from the Space's allowed booker groups
  kind: product
  actor: user
  entities:
  - entity: space
    effect: changes
    facts:
    - Allowed booker groups
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
---

# Lift a space's group restriction

## Trigger

An Areas administrator lets more people book a Space.

## Outcome

The removed Groups no longer restrict the Space; with none left, every User allowed in the Area may book it.
