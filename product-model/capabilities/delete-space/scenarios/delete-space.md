---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a Space on the Area's floor plan and saves the Area
  kind: actor
  actor: user
  entities:
  - entity: space
    effect: reads
    facts:
    - Name
  - entity: area
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product removes the Space with its bookings and Recurring bookings
  kind: product
  actor: user
  entities:
  - entity: space
    effect: removes
  - entity: booking
    as: confirmed-booking
    effect: removes
    from: Confirmed
    with: space
  - entity: booking
    as: pending-booking
    effect: removes
    from: Pending approval
    with: space
  - entity: recurring-booking
    effect: removes
    with: space
  contexts:
    web:
      place: web::administration::area-editor
---

# Delete a space

## Trigger

An Areas administrator removes a desk, seat or room.

## Outcome

The Space and all its bookings and Recurring bookings are gone; nobody is notified.
