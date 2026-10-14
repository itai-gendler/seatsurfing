---
kind: validation
routes:
  web: Web
steps:
- text: The User sets a minimum duration for visitors above the effective maximum and saves
  kind: actor
  actor: user
  entities:
  - entity: organization
    effect: reads
    facts:
    - Public booking min duration
    - Public booking max duration
    - Min booking duration
    - Max booking duration
  - entity: visitor
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::settings
- text: The Product refuses the settings
  kind: product
  actor: user
  entities:
  - entity: organization
    effect: reads
    facts:
    - Public booking min duration
    - Public booking max duration
    - Min booking duration
    - Max booking duration
  contexts:
    web:
      place: web::administration::settings
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#IsValidPublicBookingDurationSettings
---

# Public durations that cannot be met

## Trigger

A settings administrator sets public booking durations no booking can satisfy together with the organization-wide limits.

## Outcome

Nothing is saved.
