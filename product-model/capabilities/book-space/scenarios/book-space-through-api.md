---
kind: primary
routes:
  api: REST API
steps:
- text: The service account authenticates with its username and password or API token and is read-write
  kind: condition
  entities:
  - entity: service-account
    effect: reads
    facts:
    - Access mode
  - entity: user
    as: person
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The service account sends the Space, the times, a subject and the person's email address
  kind: actor
  actor: service-account
  entities:
  - entity: space
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The Product checks the booking rules, the Space's allowed bookers and that no other booking overlaps the slot
  kind: product
  actor: service-account
  entities:
  - entity: organization
    effect: reads
    facts:
    - Max bookings per user
    - Max concurrent bookings per user
    - Max days in advance
    - Min booking duration
    - Max booking duration
  - entity: area
    effect: reads
    facts:
    - Bookable weekdays
    - Max bookings
  - entity: space
    effect: reads
    facts:
    - Allowed booker groups
    - Approver groups
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
  contexts:
    api:
      place: rest-api
- text: The Product creates the booking of the Space for that person
  kind: product
  actor: service-account
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Email address
  - entity: booking
    effect: creates
    to: Confirmed
    facts:
    - Space
    - Enter
    - Leave
    - Subject
    - Booker
    - Public request
  - entity: space
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The Product answers with the new booking's identifier and emails the person a confirmation when their booking information emails are on
  kind: product
  actor: service-account
  entities:
  - entity: user
    as: person
    effect: reads
    facts:
    - Booking information emails
    - Email address
    - Email language
  - entity: booking
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
    - Subject
  contexts:
    api:
      place: rest-api
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#create
- kind: spec
  role: intent
  target: specs/openapi.yaml
---

# Book a space for a person through the REST API

## Trigger

An integration books a Space for a person of the Organization.

## Outcome

The person holds the booking, confirmed or waiting for approval as the Space requires, and is told by email when their booking information emails are on.

## Edge cases

- A Space with approver groups creates the booking waiting for approval, as on the Booking Site.
- A service account without Bookings access Admin, or a read-only one, is refused.
