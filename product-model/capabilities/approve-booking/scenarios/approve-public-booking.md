---
kind: primary
routes:
  web: Web
steps:
- text: The User reviews a pending booking on the Approvals page
  kind: actor
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts:
    - Booker
    - Space
    - Enter
    - Leave
    - Subject
  - entity: area
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::administration::approvals
- text: The booking was requested on the public booking page and the Organization's public booking page is still open
  kind: condition
  entities:
  - entity: booking
    effect: reads
    facts:
    - Public request
  - entity: organization
    effect: reads
    facts:
    - Public booking
  contexts:
    web:
      place: web::administration::approvals
- text: The User approves the booking
  kind: actor
  actor: user
  entities:
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::approvals
- text: The Product confirms the booking
  kind: product
  actor: user
  entities:
  - entity: booking
    effect: changes
    from: Pending approval
    to: Confirmed
    facts: []
  contexts:
    web:
      place: web::administration::approvals
- text: The Product emails the Visitor the approval with a calendar file and the details link
  kind: product
  actor: user
  entities:
  - entity: visitor
    effect: reads
    facts:
    - Email address
    - Language
    - Details link
  - entity: booking
    effect: reads
    facts:
    - Space
    - Enter
    - Leave
    - Subject
  contexts:
    web:
      place: web::administration::approvals
---

# Approve a public booking

## Trigger

A booking a visitor requested waits for approval.

## Outcome

The booking is confirmed and the visitor receives an approval email with a calendar file and the link to the booking's details page.
