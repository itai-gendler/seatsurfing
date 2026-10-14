---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a booking in the Bookings list and confirms
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
  contexts:
    web:
      place: web::administration::bookings
- text: The booking has not ended
  kind: condition
  entities:
  - entity: booking
    effect: reads
    facts:
    - Leave
  contexts:
    web:
      place: web::administration::bookings
- text: The Product removes the booking and its CalDAV entry
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: removes
    from: Confirmed
  contexts:
    web:
      place: web::administration::bookings
- text: The Product emails the booker that the booking was cancelled when their booking information emails are on
  kind: product
  actor: user
  entities:
  - entity: user
    as: booker
    effect: reads
    facts:
    - Booking information emails
    - Email address
    - Email language
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::bookings
---

# Delete someone else's booking

## Trigger

A bookings administrator removes another person's booking.

## Outcome

The booking is gone; its booker is told by email when their booking information emails are on.
