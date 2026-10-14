---
appliesTo:
- type: entity
  id: booking
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
- related:
  - verb: requests
    entity: visitor
  when:
  - state: Confirmed
- actors:
  - user
  when:
  - entity: user
    fact: Approvals access
    is: Admin
  - state: Pending approval
- related:
  - verb: holds
    entity: space
  - verb: is-approved-by
    entity: group
  - verb: includes
    entity: user
  when:
  - entity: user
    fact: Approvals access
    is: Write
  - state: Pending approval
- actors:
  - user
  when:
  - entity: user
    fact: Approvals access
    is: Write
  - entity: space
    fact: Approver groups
    absent: true
  - state: Pending approval
- unattended: true
  when:
  - entity: organization
    fact: Booking retention
    is: 'On'
- actors:
  - service-account
  when:
  - entity: service-account
    fact: Bookings access
    is: Admin
  - entity: service-account
    fact: Access mode
    is: Read-write
- actors:
  - service-account
  when:
  - entity: service-account
    fact: Approvals access
    is: Admin
  - entity: service-account
    fact: Access mode
    is: Read-write
  - state: Pending approval
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#DeleteBooking
- kind: code
  role: implementation
  target: server/router/booking-router.go#approveBooking
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#deleteBooking
- kind: code
  role: implementation
  target: server/repository/booking-repository.go#PurgeOldBookings
---

# A booking is removed by its booker, a bookings administrator, or an approver while it is pending

The User a booking is for cancels it, and a User with Bookings access Admin deletes any booking of the Organization. A visitor cancels their own booking from its details link once it is approved. Approvers who may confirm a pending booking may decline it, which removes it. The Product itself deletes bookings past the Organization's retention while booking retention is on. Read-write service accounts do the same through the REST API with Bookings access Admin, or Approvals access Admin for pending bookings.
