---
kind: primary
routes:
  web: Web
steps:
- text: The User switches approval notifications on the Approvals page
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Approval notifications
  contexts:
    web:
      place: web::administration::approvals
- text: The Product saves the User's approval notifications preference
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Approval notifications
  contexts:
    web:
      place: web::administration::approvals
---

# Switch approval notifications

## Trigger

An approver wants, or no longer wants, an email for each booking they may approve.

## Outcome

The approver receives, or stops receiving, an email for each new pending booking of their Spaces.
