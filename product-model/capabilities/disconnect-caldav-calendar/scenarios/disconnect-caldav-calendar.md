---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Disconnect
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
- text: The Product forgets the calendar connection
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

# Disconnect a CalDAV calendar

## Trigger

A User no longer wants bookings written to their calendar.

## Outcome

New and changed bookings no longer reach the calendar.
