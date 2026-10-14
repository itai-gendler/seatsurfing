---
entities:
- entity: organization
  shows:
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
  - Groups feature
  - Recurring bookings feature
  - Public booking feature
  - Kiosk mode feature
  - Identity providers feature
  - Unlimited users feature
  collects:
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
- entity: identity-provider
  shows:
  - Name
entryPoints:
- web: /ui/admin/settings/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/settings/index.tsx
- kind: code
  role: implementation
  target: server/router/settings-router.go
---

# Settings

The Organization's settings page: booking rules, security, reports, kiosk mode, public booking and retention settings saved together, the plan features, and the list of identity providers.
