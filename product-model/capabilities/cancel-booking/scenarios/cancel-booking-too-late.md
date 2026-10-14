---
kind: validation
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
- text: The cancellation deadline is on and the booking starts in fewer hours than Max hours to cancel before start
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
  contexts:
    web:
      place: web::booking-site::my-bookings
- text: The Product refuses the cancellation
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::my-bookings
---

# Cancellation refused after the deadline

## Trigger

A User tries to cancel a booking closer to its start than the Organization allows.

## Outcome

The booking stays; the User is told they cannot cancel less than the set number of hours before and to contact an administrator.

## Edge cases

- A booking that has already ended is never cancelled.
