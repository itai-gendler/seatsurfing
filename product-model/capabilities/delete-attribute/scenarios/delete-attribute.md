---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on the attribute and confirms
  kind: actor
  actor: user
  entities:
  - entity: attribute
    effect: reads
    facts:
    - Label
  contexts:
    web:
      place: web::administration::attribute-editor
- text: The Product removes the attribute and the values Spaces and Areas held for it
  kind: product
  actor: user
  entities:
  - entity: attribute
    effect: removes
  - entity: space
    effect: changes
    facts:
    - Attribute values
  - entity: area
    effect: changes
    facts:
    - Attribute values
  contexts:
    web:
      place: web::administration::attribute-editor
---

# Delete an attribute

## Trigger

An administrator no longer needs an attribute.

## Outcome

The attribute and its values are gone.
