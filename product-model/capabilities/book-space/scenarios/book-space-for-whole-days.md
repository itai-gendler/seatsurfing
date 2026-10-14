---
kind: primary
routes:
  web: Web
steps:
- text: The Organization books on a daily basis
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Daily basis booking
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The User picks an Area and the first and last day, without times
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
- text: The Product checks that the booking covers whole days within the Organization's limits, the Area's bookable weekdays and capacity and the Space's allowed bookers, and that no other booking overlaps
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
    - Daily basis booking
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
- text: The Space has no approver groups
  kind: condition
  entities:
  - entity: space
    effect: reads
    facts:
    - Approver groups
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site::book-a-space
- text: The Product creates a confirmed booking of the Space for the User
  kind: product
  actor: user
  entities:
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
      place: web::booking-site::book-a-space
- text: The Product emails the User a confirmation with a calendar file when their booking information emails are on, and adds the booking to their CalDAV calendar when they connected one
  kind: product
  actor: user
  entities:
  - entity: user
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
      place: web::booking-site::book-a-space
---

# Book a free space for whole days

## Trigger

A User of an Organization that books on a daily basis needs a Space for one or more days.

## Outcome

The User holds a confirmed booking of the Space covering whole days.

## Edge cases

- With daily basis booking the maximum booking duration rounds up to whole days.
