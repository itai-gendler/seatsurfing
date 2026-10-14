---
kind: primary
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
- text: The Product checks the Organization's limits, the Area's bookable weekdays and capacity and the Space's allowed bookers, and that no other booking overlaps the slot
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
    - Subject required
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Space has approver groups and the Organization's plan includes Groups
  kind: condition
  entities:
  - entity: space
    effect: reads
    facts:
    - Approver groups
  - entity: organization
    effect: reads
    facts:
    - Groups feature
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product creates the booking of the Space for the User, waiting for approval
  kind: product
  actor: user
  entities:
  - entity: space
    effect: reads
    facts: []
  - entity: booking
    effect: creates
    to: Pending approval
    facts:
    - Space
    - Enter
    - Leave
    - Subject
    - Booker
    - Public request
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product tells the User the booking needs to be confirmed first
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product emails each member of the Space's approver groups whose approval notifications are on
  kind: product
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Members
  - entity: user
    as: approver
    effect: reads
    facts:
    - Approval notifications
    - Email address
    - Email language
  - entity: booking
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
    - Subject
    - Booker
  - entity: space
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::book-a-space
---

# Book a space that needs approval

## Trigger

A User books a Space that has approver groups.

## Outcome

The User holds a booking that waits for approval and already keeps the slot from others; the approvers who asked for notifications know about it.

## Edge cases

- Approvers who never turned on approval notifications receive no email and find the request on their Approvals page.
