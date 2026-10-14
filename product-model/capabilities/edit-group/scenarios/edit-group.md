---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the Group's name and saves
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::group-editor
- text: The Product renames the Group
  kind: product
  actor: user
  entities:
  - entity: group
    effect: changes
    facts:
    - Name
  contexts:
    web:
      place: web::administration::group-editor
---

# Rename a group

## Trigger

A Groups administrator changes a Group's name.

## Outcome

The Group carries its new name wherever it is named as approver or allowed booker.
