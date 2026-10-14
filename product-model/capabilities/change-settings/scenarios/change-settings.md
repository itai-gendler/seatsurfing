---
kind: primary
routes:
  web: Web
steps:
- text: The User changes limits, durations, retention or the settings for visitors and saves
  kind: actor
  actor: user
  entities:
  - entity: organization
    effect: reads
    facts:
    - Max bookings per user
    - Max concurrent bookings per user
    - Max days in advance
    - Min booking duration
    - Max booking duration
    - Daily basis booking
    - Don't restrict admins
    - Cancellation deadline
    - Max hours to cancel before start
    - Show bookers' names
    - Hide disallowed areas
    - Subject for bookings
    - Allow recurring bookings
    - Allow bookings for non-existing users
    - Default time zone
    - Booking retention
    - Retention days
    - Disable buddies
    - Booking information emails for new users
    - Enforce second factor
    - Hide reports
    - Hide statistics
    - Target utilization
    - Kiosk mode
    - Kiosk secret
    - Public booking
    - Public booking shows floor plan
    - Public booking shows availability
    - Public booking min duration
    - Public booking max duration
    - Allow any user
  - entity: visitor
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::settings
- text: The Product checks each value is within its allowed range and saves the settings
  kind: product
  actor: user
  entities:
  - entity: organization
    effect: changes
    facts:
    - Max bookings per user
    - Max concurrent bookings per user
    - Max days in advance
    - Min booking duration
    - Max booking duration
    - Daily basis booking
    - Don't restrict admins
    - Cancellation deadline
    - Max hours to cancel before start
    - Show bookers' names
    - Hide disallowed areas
    - Subject for bookings
    - Allow recurring bookings
    - Allow bookings for non-existing users
    - Default time zone
    - Booking retention
    - Retention days
    - Disable buddies
    - Booking information emails for new users
    - Enforce second factor
    - Hide reports
    - Hide statistics
    - Target utilization
    - Kiosk mode
    - Kiosk secret
    - Public booking
    - Public booking shows floor plan
    - Public booking shows availability
    - Public booking min duration
    - Public booking max duration
    - Allow any user
  contexts:
    web:
      place: web::administration::settings
---

# Change the booking rules

## Trigger

A settings administrator adjusts the Organization's booking rules.

## Outcome

The Organization keeps the new settings; bookings made or changed from now on follow them, while existing bookings stay.

## Edge cases

- Retention days lie between 30 and 999, public booking durations between 0 and 24 hours.
