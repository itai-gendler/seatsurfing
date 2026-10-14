---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a person and confirms
  kind: actor
  actor: user
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::administration::user-editor
- text: The person is not the User themselves and another administrator remains
  kind: condition
  entities:
  - entity: user
    as: person
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product removes the person with their bookings, buddies and passkeys and takes them out of their Groups
  kind: product
  actor: user
  entities:
  - entity: user
    as: person
    effect: removes
  - entity: booking
    as: confirmed-booking
    effect: removes
    from: Confirmed
    with: person
  - entity: booking
    as: pending-booking
    effect: removes
    from: Pending approval
    with: person
  - entity: buddy
    effect: removes
    with: person
  - entity: passkey
    effect: removes
    with: person
  - entity: group
    effect: changes
    facts:
    - Members
  contexts:
    web:
      place: web::administration::user-editor
- text: The Product removes the person's recurring bookings
  kind: product
  actor: user
  entities:
  - entity: recurring-booking
    effect: removes
  contexts:
    web:
      place: web::administration::user-editor
---

# Delete a user

## Trigger

A person leaves the Organization.

## Outcome

The User, their bookings, series, buddies and passkeys are gone, they are no longer in any Group or Role, and they can no longer sign in.
