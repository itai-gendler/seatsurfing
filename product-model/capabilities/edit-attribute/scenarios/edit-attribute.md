---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the attribute and saves
  kind: actor
  actor: user
  entities:
  - entity: attribute
    effect: reads
    facts:
    - Label
    - Type
  contexts:
    web:
      place: web::administration::attribute-editor
- text: The Product changes the attribute
  kind: product
  actor: user
  entities:
  - entity: attribute
    effect: changes
    facts:
    - Label
    - Type
    - Applies to spaces
    - Applies to areas
  contexts:
    web:
      place: web::administration::attribute-editor
---

# Edit an attribute

## Trigger

An administrator renames an attribute or changes where it applies.

## Outcome

The attribute carries its new settings.
