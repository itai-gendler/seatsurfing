---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the colleague's email address, the Area, the Space, the times and a subject
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
- text: No User has the email address, the Organization allows bookings for non-existing users and the address belongs to one of the Organization's domains
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Allow bookings for non-existing users
  - entity: booking
    effect: reads
    facts: []
  - entity: user
    as: colleague
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::booking-editor
- text: The Product creates a User with that email address
  kind: product
  actor: user
  entities:
  - entity: user
    as: colleague
    effect: creates
    facts:
    - Email address
  contexts:
    web:
      place: web::administration::booking-editor
- text: The Product creates the booking of the Space for the new User
  kind: product
  actor: user
  entities:
  - entity: user
    as: colleague
    effect: reads
    facts:
    - Email address
  - entity: space
    effect: reads
    facts: []
  - entity: booking
    effect: creates
    to: Confirmed
    facts:
    - Space
    - Enter
    - Leave
    - Subject
    - Booker
    - Public request
  contexts:
    web:
      place: web::administration::booking-editor
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#bookForUser
---

# Book a space for someone without an account

## Trigger

A bookings administrator books a Space for an email address no User of the Organization has.

## Outcome

A User with that email address exists and holds the booking.

## Edge cases

- Without Allow bookings for non-existing users, an unknown email address is refused.
