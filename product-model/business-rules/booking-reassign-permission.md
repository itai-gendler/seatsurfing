---
appliesTo:
- type: entity
  id: booking
  effect: changes
  facts:
  - Booker
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Bookings access
    is: Admin
  - fact: Public request
    is: 'No'
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#update
---

# Only a bookings administrator moves a booking to another person

Changing whom a booking is for takes Bookings access Admin, and a visitor's booking is never moved to anyone.
