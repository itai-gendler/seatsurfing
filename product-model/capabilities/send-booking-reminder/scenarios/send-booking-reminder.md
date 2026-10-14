---
kind: primary
routes:
  web: Web
steps:
- text: A confirmed booking starts in 20 to 25 hours, has no reminder yet and its booker received no booking email in the last 24 hours
  kind: condition
  unattended: true
  entities:
  - entity: booking
    effect: reads
    facts:
    - Enter
    - Reminder sent
  contexts:
    web:
      place: web::booking-site
- text: The booker has booking reminders on
  kind: condition
  entities:
  - entity: user
    as: booker
    effect: reads
    facts:
    - Booking reminders
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::booking-site
- text: The Product emails the booker a reminder and records that it was sent
  kind: product
  entities:
  - entity: user
    as: booker
    effect: reads
    facts:
    - Email address
    - Email language
  - entity: booking
    effect: changes
    facts:
    - Reminder sent
  contexts:
    web:
      place: web::booking-site
---

# Remind a booker of tomorrow's booking

## Trigger

The five-minute schedule finds a confirmed booking starting in 20 to 25 hours.

## Outcome

The booker has a reminder email and the booking records when it was sent, so no second reminder follows.
