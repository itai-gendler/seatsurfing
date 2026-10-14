---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Cancel booking on an occurrence, ticks Cancel all upcoming bookings and confirms
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
- text: The Product removes the Recurring booking and each of its bookings that starts later than now, with their CalDAV entries
  kind: product
  actor: user
  entities:
  - entity: recurring-booking
    effect: removes
  - entity: booking
    effect: removes
    from: Confirmed
    with: recurring-booking
  contexts:
    web:
      place: web::booking-site::my-bookings
references:
- kind: code
  role: implementation
  target: server/repository/recurring-booking-repository.go#Delete
---

# Cancel all upcoming bookings of a series

## Trigger

A User no longer needs the Space their recurring series reserves.

## Outcome

The Recurring booking and every occurrence that has not started yet are gone; occurrences already started or past stay as single bookings.

## Edge cases

- Cancelling a whole series sends no email.
- Cancelling the last remaining occurrence one by one also removes the Recurring booking.
