---
kind: edge
routes:
  web: Web
steps:
- text: The User changes the times or Space of a booking and saves
  kind: actor
  actor: user
  entities:
  - entity: booking
    as: edited
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::booking-editor
- text: Another booking of the Space overlaps the new slot
  kind: condition
  entities:
  - entity: booking
    as: other
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::booking-editor
- text: The Product refuses the change because the slot is taken
  kind: product
  actor: user
  entities:
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::booking-editor
---

# Edit refused because the slot is taken

## Trigger

The new slot of an edited booking overlaps another booking of the Space.

## Outcome

The booking is unchanged and the User is told the slot is taken.
