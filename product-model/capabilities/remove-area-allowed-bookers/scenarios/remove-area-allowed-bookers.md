---
kind: primary
routes:
  web: Web
steps:
- text: The User removes Groups from the Area's allowed bookers and saves
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Allowed booker groups
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product removes the Groups from the Area's allowed booker groups
  kind: product
  actor: user
  entities:
  - entity: area
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

# Lift an area's group restriction

## Trigger

An Areas administrator lets more people book in an Area.

## Outcome

The removed Groups no longer restrict the Area; with no allowed booker groups left, every User may book there.
