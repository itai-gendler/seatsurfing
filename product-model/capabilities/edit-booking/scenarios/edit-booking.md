---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a booking from the Bookings list
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
- text: The User changes the Area, Space, times or subject and saves
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts: []
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::booking-editor
- text: The Product checks the booking rules and that no other booking overlaps the new slot
  kind: product
  actor: user
  entities:
  - entity: organization
    effect: reads
    facts:
    - Max bookings per user
    - Max concurrent bookings per user
    - Max days in advance
    - Min booking duration
    - Max booking duration
  - entity: area
    effect: reads
    facts:
    - Bookable weekdays
    - Max bookings
  - entity: space
    effect: reads
    facts:
    - Allowed booker groups
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
  contexts:
    web:
      place: web::administration::booking-editor
- text: The Product changes the booking
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: changes
    facts:
    - Space
    - Enter
    - Leave
    - Subject
  contexts:
    web:
      place: web::administration::booking-editor
- text: The Product emails the booker that the booking changed when their booking information emails are on
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
    facts:
    - Space
    - Enter
    - Leave
    - Subject
  contexts:
    web:
      place: web::administration::booking-editor
---

# Edit a booking

## Trigger

A bookings administrator moves a booking to other times or another Space.

## Outcome

The booking holds the new Space and times; the booker is told by email when their booking information emails are on and their CalDAV entry follows.

## Edge cases

- A booking a visitor requested opens read-only and cannot be saved.
- Entering another person's email address moves the booking to that User.
