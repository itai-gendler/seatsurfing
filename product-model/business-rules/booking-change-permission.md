---
appliesTo:
- type: entity
  id: booking
  effect: changes
  facts:
  - Space
  - Enter
  - Leave
  - Subject
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
  - fact: Public request
    is: 'No'
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#update
---

# Only the booker or a bookings administrator changes a booking, and never a visitor's

The User a booking is for, or a User with Bookings access Admin, changes its Space, times and subject. A booking a visitor requested is never changed.
