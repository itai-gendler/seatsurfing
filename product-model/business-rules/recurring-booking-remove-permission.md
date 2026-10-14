---
appliesTo:
- type: entity
  id: recurring-booking
  effect: removes
permits:
- related:
  - verb: books
    entity: user
- actors:
  - user
  when:
  - entity: user
    fact: Bookings access
    is: Admin
- unattended: true
  when:
  - entity: organization
    fact: Booking retention
    is: 'On'
- actors:
  - user
  when:
  - entity: user
    fact: Users access
    is: Admin
- actors:
  - service-account
  when:
  - entity: service-account
    fact: Users access
    is: Admin
  - entity: service-account
    fact: Access mode
    is: Read-write
references:
- kind: code
  role: implementation
  target: server/router/recurring-booking-router.go#delete
---

# Only the booker or a bookings administrator cancels a series

The User a Recurring booking is for, or a User with Bookings access Admin, cancels its upcoming occurrences. Deleting a person, which takes Users access Admin, removes their series too, and retention removes series left without bookings.
