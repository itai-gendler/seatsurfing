---
kind: primary
routes:
  web: Web
steps:
- text: The User changes defaults, notifications, language, formats, the preferred place to open or colors and saves
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Booking defaults
    - Booking information emails
    - Booking reminders
    - Email language
    - Date and time format
    - Preferred area
    - Booking colors
  contexts:
    web:
      place: web::booking-site::preferences
- text: The Product saves the User's preferences
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Booking defaults
    - Booking information emails
    - Booking reminders
    - Email language
    - Date and time format
    - Preferred area
    - Booking colors
  contexts:
    web:
      place: web::booking-site::preferences
---

# Change one's preferences

## Trigger

A User wants other defaults, notifications or colors.

## Outcome

The User's preferences are saved and the Booking Site and emails follow them.
