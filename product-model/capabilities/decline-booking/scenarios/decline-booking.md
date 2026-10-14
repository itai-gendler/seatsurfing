---
kind: primary
routes:
  web: Web
steps:
- text: The User reviews a pending booking on the Approvals page
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
    - Subject
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::approvals
- text: The User declines the booking and confirms
  kind: actor
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::approvals
- text: The Product removes the booking
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: removes
    from: Pending approval
  contexts:
    web:
      place: web::administration::approvals
- text: The Product emails the booker that the booking was declined when their booking information emails are on
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
      place: web::administration::approvals
---

# Decline a booking

## Trigger

An approver does not accept a pending booking.

## Outcome

The booking is gone and the Space is free for the slot; the booker receives a decline email when their booking information emails are on.

## Edge cases

- A visitor whose public request is declined always receives the decline email, and their details are forgotten with the booking.
- While the Organization's public booking page is closed, visitors' requests are neither approved nor declined.
