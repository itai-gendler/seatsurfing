---
kind: validation
routes:
  web: Web
steps:
- text: The kiosk display opens the Space's kiosk address
  kind: actor
  actor: kiosk
  entities:
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::kiosk
- text: The secret does not match, or kiosk mode is off for the Organization or the Space
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Kiosk mode
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
- text: The Product shows no status
  kind: product
  actor: kiosk
  entities: []
  contexts:
    web:
      place: web::public::kiosk
---

# Kiosk display refused

## Trigger

A kiosk display presents a wrong or no secret, or kiosk mode is off for the Space.

## Outcome

The display shows that the Space is not found or kiosk mode is not enabled, and no booking.
