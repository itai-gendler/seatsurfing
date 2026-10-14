---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a Group from the Groups list
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::groups
- text: The User enters the Group's name and saves
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::group-editor
- text: The Product creates the Group and opens it in the group editor
  kind: product
  actor: user
  entities:
  - entity: group
    effect: creates
    facts:
    - Name
    - Members
  contexts:
    web:
      place: web::administration::group-editor
---

# Create a group

## Trigger

A Groups administrator needs a new set of people to name as approvers or allowed bookers.

## Outcome

The Group exists and opens in the group editor, where members can be added.

## Edge cases

- An Organization whose plan does not include Groups is refused.
