---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Cancel booking on one of their bookings and confirms
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
- text: The booking has not ended and the cancellation deadline is not passed
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Cancellation deadline
    - Max hours to cancel before start
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
  contexts:
    web:
      place: web::booking-site::my-bookings
- text: The Product removes the booking and its CalDAV entry
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: removes
    from: Confirmed
  contexts:
    web:
      place: web::booking-site::my-bookings
- text: The Product emails the User that the booking was cancelled when their booking information emails are on
  kind: product
  actor: user
  entities:
  - entity: user
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
      place: web::booking-site::my-bookings
---

# Cancel one's own booking

## Trigger

A User no longer needs a booked Space.

## Outcome

The booking is gone and the Space is free again for the slot; the User is told by email when their booking information emails are on.

## Edge cases

- A booking that still waits for approval is cancelled the same way.
- The same cancellation is offered on the User's own booking on the floor plan.
