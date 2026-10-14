---
kind: primary
routes:
  web: Web
steps:
- text: The User adds Groups to the Area's allowed bookers and saves
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
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product adds the Groups to the Area's allowed booker groups
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

# Restrict an area to groups

## Trigger

An Areas administrator limits who may book in an Area.

## Outcome

Only members of the Area's allowed booker groups book its Spaces; where the Organization hides disallowed areas, others no longer see it on the Booking Site.
