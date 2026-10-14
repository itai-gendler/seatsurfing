---
kind: primary
routes:
  api: REST API
steps:
- text: The service account authenticates and has Bookings access Read or Admin
  kind: condition
  entities:
  - entity: service-account
    effect: reads
    facts:
    - Bookings access
  - entity: booking
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The service account asks for bookings between two times, optionally for an Area and people
  kind: actor
  actor: service-account
  entities:
  - entity: area
    effect: reads
    facts: []
  - entity: booking
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The Product answers with the matching bookings and their bookers
  kind: product
  actor: service-account
  entities:
  - entity: booking
    effect: reads
    facts:
    - Booker
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
  target: server/router/booking-router.go#getFiltered
- kind: spec
  role: intent
  target: specs/openapi.yaml
---

# Read bookings through the REST API

## Trigger

An integration reads the Organization's bookings for a period.

## Outcome

The service account receives the matching bookings with their bookers.
