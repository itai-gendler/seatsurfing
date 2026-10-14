---
kind: primary
routes:
  web: Web
steps:
- text: The Organization books by time slot rather than by whole days
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Daily basis booking
  contexts:
    web:
      place: web::booking-site::book-a-space
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

# Book a free space for a time slot

## Trigger

A User needs a desk, seat or room for part of a day.

## Outcome

The User holds a confirmed booking of the Space for the chosen slot and sees it among their bookings.

## Edge cases

- The User narrows the Spaces shown by attribute values, the number of free Spaces or whether a buddy is on site; Spaces a buddy booked show in the buddy color.
- An Area or Space that is not enabled is booked only by Users with Areas access Admin.
- A Space that requires a subject refuses a booking whose subject has fewer than three characters, unless the Organization's Subject for bookings is Disabled.
