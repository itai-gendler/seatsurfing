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
- text: The Product checks the booking rules, the Space's allowed bookers and that no other booking overlaps the slot
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
- text: The Product creates the booking of the Space for the colleague
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
- text: The Product emails the colleague a confirmation when their booking information emails are on
  kind: product
  actor: user
  entities:
  - entity: user
    as: colleague
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
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#create
- kind: code
  role: implementation
  target: server/router/booking-router.go#bookForUser
- kind: code
  role: implementation
  target: ui/src/pages/admin/bookings/[id].tsx
---

# Book a space for a colleague

## Trigger

A bookings administrator books a Space on behalf of another User of the Organization.

## Outcome

The colleague holds the booking and is told about it by email when their booking information emails are on.
