---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses the calendar action on one of their bookings
  kind: actor
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
  contexts:
    web:
      place: web::booking-site::my-bookings
- text: The Product returns a calendar file for the booking, or for all occurrences of its series
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::booking-site::my-bookings
---

# Add a booking to one's calendar

## Trigger

A User wants a booking in their own calendar.

## Outcome

The User has a calendar file with the booking's Space, Area and times, or with every occurrence of the series.

## Edge cases

- The same file is offered right after booking.
