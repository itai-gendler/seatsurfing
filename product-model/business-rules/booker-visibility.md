---
appliesTo:
- type: entity
  id: booking
  effect: reads
  facts:
  - Booker
permits:
- related:
  - verb: books
    entity: user
- actors:
  - user
  when:
  - entity: user
    fact: Bookings access
    is-not: None
- actors:
  - user
  when:
  - entity: user
    fact: Approvals access
    is-not: None
  - state: Pending approval
- actors:
  - user
  when:
  - entity: organization
    fact: Show bookers' names
    is: 'On'
- actors:
  - user
  when:
  - entity: user
    fact: Presence report access
    is: Read
- actors:
  - kiosk
  when:
  - entity: organization
    fact: Show bookers' names
    is: 'On'
- actors:
  - service-account
  when:
  - entity: service-account
    fact: Bookings access
    is-not: None
references:
- kind: code
  role: implementation
  target: server/service/space-service.go#GetAvailabilityForUser
- kind: code
  role: implementation
  target: server/service/booking-service.go#GetFiltered
- kind: code
  role: implementation
  target: server/service/booking-service.go#GetPendingApprovals
---

# Only the booker and those the Organization lets read bookings see who booked

A User sees who a booking is for when it is their own, when they have Bookings access Read or Admin, when they may decide it while it is pending, or when the Organization shows bookers' names to everyone; the presence report shows bookers to its readers, a kiosk display only where names are shown, and service accounts with Bookings access Read or Admin read them through the REST API.
