---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses a period of up to 31 days and optionally an Area
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::analysis
- text: The Organization does not hide reports
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Hide reports
  contexts:
    web:
      place: web::administration::analysis
- text: The Product lists each person with a booking in the period and their days present
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Booker
    - Enter
  contexts:
    web:
      place: web::administration::analysis
- text: The User reads and downloads the report
  kind: actor
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Booker
    - Enter
  contexts:
    web:
      place: web::administration::analysis
---

# Read the presence report

## Trigger

An administrator wants to know who was in the office.

## Outcome

The administrator sees, per person and day, whether they had a booking, and can download it.

## Edge cases

- A period longer than 31 days is refused.
