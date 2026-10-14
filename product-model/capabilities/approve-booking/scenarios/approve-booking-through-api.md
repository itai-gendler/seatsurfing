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
    as: booker
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The service account approves a pending booking
  kind: actor
  actor: service-account
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The Product confirms the booking
  kind: product
  actor: service-account
  entities:
  - entity: booking
    effect: changes
    from: Pending approval
    to: Confirmed
    facts: []
  contexts:
    api:
      place: rest-api
- text: The Product emails the booker that the booking was approved when their booking information emails are on
  kind: product
  actor: service-account
  entities:
  - entity: user
    as: booker
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
  target: server/router/booking-router.go#approveBooking
- kind: spec
  role: intent
  target: specs/openapi.yaml
---

# Approve a booking through the REST API

## Trigger

An integration confirms a pending booking.

## Outcome

The booking is confirmed and its booker is told as on the Approvals page.
