---
appliesTo:
- type: entity
  id: recurring-booking
  effect: creates
permits:
- related:
  - verb: books
    entity: user
  when:
  - entity: organization
    fact: Allow recurring bookings
    is: 'On'
  - entity: organization
    fact: Recurring bookings feature
    is: 'On'
  - entity: space
    fact: Enabled
    is: 'Yes'
  - entity: area
    fact: Enabled
    is: 'Yes'
references:
- kind: code
  role: implementation
  target: server/router/recurring-booking-router.go#create
---

# People book a recurring series for themselves while recurring bookings are allowed

A User books a recurring series of an enabled Space in an enabled Area for themselves only, and only while the Organization's plan includes recurring bookings and the Organization allows them. Nobody books a series for someone else.
