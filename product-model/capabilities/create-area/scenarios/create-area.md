---
kind: primary
routes:
  web: Web
steps:
- text: The User adds an Area from the Areas list
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::areas
- text: The User enters the Area's name, description, time zone, capacity, bookable weekdays and floor plan and saves
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product creates the Area
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
---

# Create an area

## Trigger

An Areas administrator sets up a new floor or office.

## Outcome

The Area exists and opens in the area editor, ready for Spaces.

## Edge cases

- An unknown time zone or weekday is refused.
- An Area without a time zone reads its times in the Organization's default time zone.
