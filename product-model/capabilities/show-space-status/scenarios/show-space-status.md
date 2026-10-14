---
kind: primary
routes:
  web: Web
steps:
- text: The kiosk display opens the Space's kiosk address presenting the kiosk secret
  kind: actor
  actor: kiosk
  entities:
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::kiosk
- text: The secret matches, kiosk mode is on and the Space shows on a kiosk display
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Kiosk mode
    - Kiosk secret
    - Kiosk mode feature
  - entity: space
    effect: reads
    facts:
    - Kiosk display
  - entity: kiosk
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::kiosk
- text: The Product shows the Space's status with its current and next booking, and their bookers' names where the Organization shows bookers' names
  kind: product
  actor: kiosk
  entities:
  - entity: space
    effect: reads
    facts:
    - Name
  - entity: area
    effect: reads
    facts:
    - Name
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
    - Subject
    - Booker
  - entity: organization
    effect: reads
    facts:
    - Show bookers' names
  contexts:
    web:
      place: web::public::kiosk
---

# Show a room's status beside it

## Trigger

A kiosk display beside a Space opens its kiosk address with the Organization's kiosk secret.

## Outcome

The display shows whether the Space is free or occupied, the current and the next booking, with bookers' names where the Organization shows them.
