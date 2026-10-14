---
kind: edge
routes:
  web: Web
steps:
- text: The Visitor picks a day, a time slot and a Space opened for public booking, on the floor plan or from the list
  kind: actor
  actor: visitor
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  - entity: space
    effect: reads
    facts:
    - Name
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::public-booking
- text: The Visitor enters their name, email address and a subject if wanted and requests the booking
  kind: actor
  actor: visitor
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::public-booking
- text: The Product checks the slot lies within one day, the public and organization-wide duration limits, the advance limit and the Area's bookable weekdays
  kind: product
  actor: visitor
  entities:
  - entity: organization
    effect: reads
    facts:
    - Public booking min duration
    - Public booking max duration
    - Min booking duration
    - Max booking duration
    - Max days in advance
  - entity: area
    effect: reads
    facts:
    - Bookable weekdays
  contexts:
    web:
      place: web::public::public-booking
- text: The Product emails the Visitor a confirmation link valid for 30 minutes
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::public-booking
- text: The Visitor opens the confirmation link
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::public-booking
- text: Another booking of the Space overlaps the slot or the Area is full
  kind: condition
  entities:
  - entity: booking
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
  - entity: area
    effect: reads
    facts:
    - Max bookings
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::public-booking
- text: The Product reports that the Space is no longer available for the slot
  kind: product
  actor: visitor
  entities:
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::public-booking
---

# Confirmation finds the slot taken

## Trigger

Someone else booked the Space for the slot before the visitor confirmed.

## Outcome

No booking is created and the visitor is told the Space is no longer available and may request a new booking.
