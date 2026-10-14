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
- text: Another booking of the Space, confirmed or waiting for approval, overlaps the slot
  kind: condition
  entities:
  - entity: booking
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product refuses the booking because the slot is taken
  kind: product
  actor: user
  entities:
  - entity: space
    effect: reads
    facts: []
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::book-a-space
---

# Booking refused because the slot is taken

## Trigger

Another booking of the Space overlaps the slot by the time the User confirms.

## Outcome

Nothing is booked and the User is told another booking already covers the slot.

## Edge cases

- Back-to-back bookings, one ending when the next starts, do not overlap.
