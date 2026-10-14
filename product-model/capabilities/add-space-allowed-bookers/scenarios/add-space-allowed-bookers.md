---
kind: primary
routes:
  web: Web
steps:
- text: The User adds Groups to the Space's allowed bookers and saves the Area
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
- text: The Product adds the Groups to the Space's allowed booker groups
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

# Restrict a space to groups

## Trigger

An Areas administrator reserves a Space for some Groups.

## Outcome

Only members of the Space's allowed booker groups book it; others see it as not allowed on the floor plan.
