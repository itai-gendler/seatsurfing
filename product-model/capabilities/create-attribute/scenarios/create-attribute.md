---
kind: primary
routes:
  web: Web
steps:
- text: The User adds an attribute from the attributes list
  kind: actor
  actor: user
  entities:
  - entity: attribute
    effect: reads
    facts:
    - Label
  contexts:
    web:
      place: web::administration::attributes
- text: The User enters its label and type, chooses where it applies and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::administration::attribute-editor
- text: The Product creates the attribute
  kind: product
  actor: user
  entities:
  - entity: attribute
    effect: creates
    facts:
    - Label
    - Type
    - Applies to spaces
    - Applies to areas
  contexts:
    web:
      place: web::administration::attribute-editor
---

# Create an attribute

## Trigger

An administrator wants people to find Spaces by a property.

## Outcome

The attribute exists; Area and Space editors offer a value for it and search can filter by it.
