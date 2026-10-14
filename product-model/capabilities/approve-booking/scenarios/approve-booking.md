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
- text: The Product emails the booker that the booking was approved when their booking information emails are on, and adds it to their CalDAV calendar
  kind: product
  actor: user
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
    web:
      place: web::administration::approvals
---

# Approve a booking

## Trigger

A booking a User made waits for approval.

## Outcome

The booking is confirmed; the booker receives an approval email with a calendar file when their booking information emails are on, and the booking reaches their CalDAV calendar.

## Edge cases

- Approving a booking another approver already approved changes nothing.
