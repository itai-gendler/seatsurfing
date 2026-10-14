---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses a period such as today, this week or a range, and optionally an Area and people
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::bookings
- text: The Product lists the Organization's bookings in the period matching the filters
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Booker
    - Space
    - Enter
    - Leave
    - Subject
  - entity: organization
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::bookings
- text: The User reads the list and downloads it
  kind: actor
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Booker
    - Space
    - Enter
    - Leave
    - Subject
  contexts:
    web:
      place: web::administration::bookings
---

# Browse the organization's bookings

## Trigger

A bookings reader wants to see who booked what in a period.

## Outcome

The User sees the matching bookings with their bookers and can download them as a spreadsheet.

## Edge cases

- Current bookings lists the bookings under way right now.
- A person filter naming an address no User of the Organization has is refused.
