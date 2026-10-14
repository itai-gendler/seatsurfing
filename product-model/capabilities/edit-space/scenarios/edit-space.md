---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the Space's settings, attribute values or position and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: space
    effect: reads
    facts:
    - Name
    - Position on floor plan
    - Enabled
    - Subject required
    - Public booking
    - Kiosk display
    - Attribute values
  - entity: area
    effect: reads
    facts: []
  - entity: attribute
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product changes the Space
  kind: product
  actor: user
  entities:
  - entity: space
    effect: changes
    facts:
    - Name
    - Position on floor plan
    - Enabled
    - Subject required
    - Public booking
    - Kiosk display
    - Attribute values
  contexts:
    web:
      place: web::administration::area-editor
---

# Edit a space

## Trigger

An Areas administrator changes a Space's settings or moves it on the floor plan.

## Outcome

The Space keeps its new settings; later bookings follow them.

## Edge cases

- Disabling a Space keeps it bookable for Users with Areas access Admin only.
