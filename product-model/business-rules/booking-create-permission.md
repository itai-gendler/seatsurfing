---
appliesTo:
- type: entity
  id: booking
  effect: creates
permits:
- related: &id001
  - verb: books
    entity: user
  when:
  - &id002
    entity: space
    fact: Enabled
    is: 'Yes'
  - &id003
    entity: area
    fact: Enabled
    is: 'Yes'
- related: *id001
  when:
  - entity: user
    fact: Areas access
    is: Admin
- actors:
  - user
  when:
  - entity: user
    fact: Bookings access
    is: Admin
  - *id002
  - *id003
- actors:
  - user
  when:
  - entity: user
    fact: Bookings access
    is: Admin
  - entity: user
    fact: Areas access
    is: Admin
- related:
  - verb: requests
    entity: visitor
  when:
  - entity: space
    fact: Public booking
    is: 'On'
  - entity: organization
    fact: Public booking
    is: 'On'
  - entity: organization
    fact: Public booking feature
    is: 'On'
  - *id002
  - *id003
- actors:
  - service-account
  when:
  - entity: service-account
    fact: Bookings access
    is: Admin
  - entity: service-account
    fact: Access mode
    is: Read-write
  - *id002
  - *id003
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#PrepareCreate
- kind: code
  role: implementation
  target: server/router/booking-router.go#create
- kind: code
  role: implementation
  target: server/router/booking-router.go#bookForUser
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#confirm
---

# People book for themselves; bookings administrators also book for others

Every signed-in User books an enabled Space in an enabled Area for themselves; a User with Areas access Admin also books disabled ones. A User with Bookings access Admin books for any person of the Organization. A visitor requests a Space only while it is open to public booking, the Organization's public booking page is open and its plan includes public booking. A read-write service account with Bookings access Admin books enabled Spaces for people through the REST API.
