---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses a period, a person or an outcome
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::administration::audit-log
- text: The Product lists the matching sign-in attempts, newest first
  kind: product
  actor: user
  entities:
  - entity: audit-entry
    effect: reads
    facts:
    - Time
    - Email address
    - Method
    - Outcome
    - Device
    - Identity provider
  contexts:
    web:
      place: web::administration::audit-log
- text: The User reads an attempt's details
  kind: actor
  actor: user
  entities:
  - entity: audit-entry
    effect: reads
    facts:
    - Time
    - Email address
    - Method
    - Outcome
    - Device
  contexts:
    web:
      place: web::administration::audit-log
---

# Read the audit log

## Trigger

An administrator wants to see who signed in, or tried to.

## Outcome

The administrator sees the matching sign-in attempts with their outcome.
