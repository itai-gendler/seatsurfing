---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the dashboard and picks an Area or all Areas
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::dashboard
- text: The Organization does not hide statistics
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Hide statistics
    - Target utilization
  contexts:
    web:
      place: web::administration::dashboard
- text: The Product shows the counts, utilization and bookings by weekday
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
  contexts:
    web:
      place: web::administration::dashboard
---

# Read the dashboard

## Trigger

An administrator wants to know how the office is used.

## Outcome

The administrator sees the counts and utilization figures.
