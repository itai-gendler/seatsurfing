---
kind: edge
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
- text: The User turns on recurrence and chooses a daily cadence every few days or a weekly cadence on chosen weekdays every few weeks, and an end date
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product checks every occurrence of the series against the same rules as a single booking and shows how many are available
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
    - Allow recurring bookings
    - Recurring bookings feature
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
- text: The Product reports how many occurrences are not available and asks whether to book the available ones anyway
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The User applies the recurrence anyway
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product creates the Recurring booking and a booking of the Space for each available occurrence, skipping the others
  kind: product
  actor: user
  entities:
  - entity: space
    effect: reads
    facts: []
  - entity: recurring-booking
    effect: creates
    facts:
    - Space
    - Enter
    - Leave
    - Subject
    - Cadence
    - Cycle
    - Weekdays
    - End date
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
    with: recurring-booking
  contexts:
    web:
      place: web::booking-site::book-a-space
references:
- kind: code
  role: implementation
  target: server/router/recurring-booking-router.go#create
---

# Book the available occurrences of a series

## Trigger

Some occurrences of the series a User wants are already taken or break a booking rule.

## Outcome

The User holds a Recurring booking with bookings for the available occurrences only; the unavailable ones are left out and reported.
