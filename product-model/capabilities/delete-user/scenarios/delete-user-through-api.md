---
kind: primary
routes:
  api: REST API
steps:
- text: The service account authenticates, is read-write and has Users access Admin
  kind: condition
  entities:
  - entity: service-account
    effect: reads
    facts:
    - Access mode
    - Users access
  - entity: user
    as: person
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The service account asks to delete a User
  kind: actor
  actor: service-account
  entities:
  - entity: user
    as: person
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The Product removes the User with their bookings, buddies and passkeys and takes them out of their Groups
  kind: product
  actor: service-account
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
    api:
      place: rest-api
- text: The Product removes the User's recurring bookings
  kind: product
  actor: service-account
  entities:
  - entity: recurring-booking
    effect: removes
  - entity: user
    as: person
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
references:
- kind: spec
  role: intent
  target: specs/openapi.yaml
---

# Remove a user through the REST API

## Trigger

An integration removes a person who left.

## Outcome

The User and everything that belonged to them are gone.
