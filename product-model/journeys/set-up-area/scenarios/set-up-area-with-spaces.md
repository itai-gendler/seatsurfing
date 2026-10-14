---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User enters the new Area's name, time zone, capacity, bookable weekdays and floor plan and saves
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
  capability: create-area
- text: The Product creates the Area and opens it in the area editor with its floor plan
  kind: product
  actor: user
  entities:
  - entity: area
    effect: creates
    facts:
    - Name
    - Description
    - Time zone
    - Enabled
    - Max bookings
    - Bookable weekdays
    - Floor plan
    - Attribute values
    - Allowed booker groups
  contexts:
    web:
      place: web::administration::area-editor
  capability: create-area
- text: The User draws Spaces on the Area's floor plan, names them and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Floor plan
  - entity: space
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::area-editor
  capability: create-space
- text: The Product creates the Spaces in the Area
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
  capability: create-space
---

# Create an area and draw its spaces

## Trigger

An Areas administrator opens a new floor or office for booking.

## Outcome

The Area exists with its first Spaces, ready to be booked.
