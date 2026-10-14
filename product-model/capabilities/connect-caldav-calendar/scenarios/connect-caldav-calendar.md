---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the CalDAV address, username and password and asks for their calendars
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - CalDAV calendar
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product connects to the calendar server and lists the User's calendars
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::preferences
- text: The User picks a calendar and connects it
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product keeps the connection, the password encrypted
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - CalDAV calendar
  contexts:
    web:
      place: web::booking-site::preferences
---

# Connect a CalDAV calendar

## Trigger

A User wants their bookings in their own calendar automatically.

## Outcome

The User's bookings are written to the chosen calendar from now on.

## Edge cases

- A calendar server that cannot be reached or refuses the credentials shows an error and nothing is kept.
