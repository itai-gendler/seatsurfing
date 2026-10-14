---
kind: primary
routes:
  web: Web
steps:
- text: The Organization keeps booking retention on and has bookings that ended more than its retention days, and at least 30 days, ago
  kind: condition
  unattended: true
  entities:
  - entity: organization
    effect: reads
    facts:
    - Booking retention
    - Retention days
  - entity: booking
    as: confirmed-booking
    effect: reads
    facts:
    - Leave
  contexts:
    web:
      place: web::administration
- text: The Product deletes up to 100 of those bookings, oldest first
  kind: product
  entities:
  - entity: booking
    as: confirmed-booking
    effect: removes
    from: Confirmed
  - entity: booking
    as: pending-booking
    effect: removes
    from: Pending approval
  contexts:
    web:
      place: web::administration
- text: The Product deletes Recurring bookings left without bookings
  kind: product
  entities:
  - entity: recurring-booking
    effect: removes
  - entity: booking
    as: confirmed-booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration
- text: The Product forgets visitor details left without a booking
  kind: product
  entities:
  - entity: visitor
    effect: removes
  - entity: booking
    as: confirmed-booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration
---

# Delete bookings past retention

## Trigger

The minute schedule runs while an Organization keeps booking retention on.

## Outcome

Bookings that ended more than the retention days ago are gone, up to 100 per run, with Recurring bookings and visitor details nothing refers to any more.
