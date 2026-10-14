---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete in the area editor and confirms that everything in the Area will be lost
  kind: actor
  actor: user
  entities:
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::area-editor
- text: The Product removes the Area with its Spaces and their bookings and Recurring bookings
  kind: product
  actor: user
  entities:
  - entity: area
    effect: removes
  - entity: space
    effect: removes
    with: area
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

# Delete an area

## Trigger

An Areas administrator no longer needs an Area.

## Outcome

The Area, its Spaces and all their bookings and Recurring bookings are gone; nobody is notified.
