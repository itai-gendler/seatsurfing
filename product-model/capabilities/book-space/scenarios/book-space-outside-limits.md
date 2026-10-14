---
kind: validation
routes:
  web: Web
steps:
- text: The User picks an Area, a day and a time slot
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product shows each Space of the Area on the floor plan as free, booked, booked by the User or not allowed, and marks those that need approval
  kind: product
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
    - Floor plan
  - entity: space
    effect: reads
    facts:
    - Name
    - Position on floor plan
    - Approver groups
    - Allowed booker groups
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The User selects a free Space, adds a subject if wanted and confirms
  kind: actor
  actor: user
  entities:
  - entity: space
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: 'The Product finds the booking breaks a rule: it lies in the past, too many days ahead, too short or too long, on a weekday the Area does not take, beyond the Area''s capacity or the User''s number of upcoming or concurrent bookings, or the User is not an allowed booker'
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
    - Allowed booker groups
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
      place: web::booking-site::book-a-space
- text: The Product refuses the booking and names the broken rule
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::book-a-space
---

# Booking refused by the booking rules

## Trigger

A User books a slot that breaks one of the Organization's or the Area's booking rules.

## Outcome

Nothing is booked and the User is told which rule the booking breaks.

## Edge cases

- Where the Organization does not restrict admins, a User with Bookings access Admin is spared the per-person limits, duration, advance and weekday rules.
