---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens the details link from the approval email
  kind: actor
  actor: visitor
  entities:
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
    - Space
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::public::booking-details
- text: The booking is confirmed and has not ended
  kind: condition
  entities:
  - entity: booking
    effect: reads
    facts:
    - Leave
  contexts:
    web:
      place: web::public::booking-details
- text: The Visitor chooses Cancel booking and confirms
  kind: actor
  actor: visitor
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::booking-details
- text: The Product removes the booking
  kind: product
  actor: visitor
  entities:
  - entity: booking
    effect: removes
    from: Confirmed
  contexts:
    web:
      place: web::public::booking-details
- text: The Product forgets the Visitor's details
  kind: product
  actor: visitor
  entities:
  - entity: visitor
    effect: removes
  contexts:
    web:
      place: web::public::booking-details
- text: The Product emails the Visitor that the booking was cancelled
  kind: product
  actor: visitor
  entities:
  - entity: visitor
    effect: reads
    facts:
    - Email address
    - Language
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::booking-details
references:
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#getValidDetailsBooking
---

# Cancel a public booking from its details link

## Trigger

A visitor no longer needs the Space their approved booking reserves.

## Outcome

The booking is gone, the details link stops working and the visitor receives a cancellation email.

## Edge cases

- A details link of a booking that is pending, declined, cancelled or ended shows that the link is invalid or expired.
