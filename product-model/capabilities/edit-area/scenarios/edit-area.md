---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the Area's settings, attribute values or floor plan and saves
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
    - Enabled
    - Floor plan
    - Attribute values
  - entity: attribute
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product changes the Area
  kind: product
  actor: user
  entities:
  - entity: area
    effect: changes
    facts:
    - Name
    - Description
    - Time zone
    - Enabled
    - Max bookings
    - Bookable weekdays
    - Floor plan
    - Attribute values
  contexts:
    web:
      place: web::administration::area-editor
---

# Edit an area

## Trigger

An Areas administrator changes an Area's settings or floor plan.

## Outcome

The Area keeps its new settings; later bookings follow them.

## Edge cases

- Disabling an Area keeps it bookable for Users with Areas access Admin only.
