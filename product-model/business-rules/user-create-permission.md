---
appliesTo:
- type: entity
  id: user
  effect: creates
permits:
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
- actors:
  - user
  when:
  - entity: user
    fact: Bookings access
    is: Admin
  - entity: organization
    fact: Allow bookings for non-existing users
    is: 'On'
- self: true
  when:
  - entity: organization
    fact: Allow any user
    is: 'On'
references:
- kind: code
  role: implementation
  target: server/router/user-router.go#create
- kind: code
  role: implementation
  target: server/router/booking-router.go#bookForUser
---

# Users administrators add people; bookings administrators may add them by booking

A User with Users access Admin, or a read-write service account with Users access Admin, adds people. A User with Bookings access Admin adds a person by booking for an unknown email address while the Organization allows bookings for non-existing users. A person the Organization does not know gets a User at their first sign-in through one of its identity providers while the Organization allows any user.
