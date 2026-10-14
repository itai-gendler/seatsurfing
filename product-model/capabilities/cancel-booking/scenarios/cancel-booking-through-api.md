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
- text: The service account asks to delete a booking
  kind: actor
  actor: service-account
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The booking has not ended and the cancellation deadline is not passed
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Cancellation deadline
    - Max hours to cancel before start
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Leave
  contexts:
    api:
      place: rest-api
- text: The Product removes the booking and its CalDAV entry
  kind: product
  actor: service-account
  entities:
  - entity: booking
    effect: removes
    from: Confirmed
  contexts:
    api:
      place: rest-api
- text: The Product emails the booker that the booking was cancelled when their booking information emails are on
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
    facts: []
  contexts:
    api:
      place: rest-api
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#DeleteBooking
- kind: spec
  role: intent
  target: specs/openapi.yaml
---

# Cancel a booking through the REST API

## Trigger

An integration cancels a person's booking.

## Outcome

The booking is gone and its booker is told by email when their booking information emails are on.
