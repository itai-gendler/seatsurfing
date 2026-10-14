---
kind: primary
routes:
  web: Web
steps:
- text: The User draws a Space on the Area's floor plan, names it, sets whether it is enabled, requires a subject or shows on a kiosk display and its attribute values, and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Floor plan
  - entity: space
    effect: reads
    facts: []
  - entity: attribute
    effect: reads
    facts: []
  - entity: kiosk
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product creates the Space in the Area
  kind: product
  actor: user
  entities:
  - entity: space
    effect: creates
    facts:
    - Name
    - Position on floor plan
    - Enabled
    - Subject required
    - Public booking
    - Kiosk display
    - Attribute values
    - Approver groups
    - Allowed booker groups
  - entity: area
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
---

# Create a space

## Trigger

An Areas administrator adds a desk, seat or room to an Area.

## Outcome

The Space appears on the Area's floor plan and can be booked.
