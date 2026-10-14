---
relations:
- entity: area
  verb: contains
  cardinality: one-to-many
- entity: group
  verb: defines
  cardinality: one-to-many
- entity: user
  verb: has-member
  cardinality: one-to-many
- entity: role
  verb: defines
  cardinality: one-to-many
- entity: service-account
  verb: runs
  cardinality: one-to-many
- entity: identity-provider
  verb: trusts
  cardinality: one-to-many
- entity: attribute
  verb: defines
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/api/entities.go
- kind: code
  role: implementation
  target: server/router/settings-router.go#isValidSettingNameWrite
- kind: code
  role: implementation
  target: server/app/app.go#InitializeSingleOrgSettings
---

# Organization

The tenant everything else belongs to: one company or office using Seatsurfing, with the booking rules every booking in it follows and the features its plan includes. An installation that holds a single Organization has every plan feature.

## Information kept

- **Name** — the organization's name
- **Language** — the language of the Organization's emails unless a person chose another
- **Max bookings per user** — how many upcoming bookings one person may hold
- **Max concurrent bookings per user** — how many bookings one person may hold at the same time; 0 means no limit
- **Max days in advance** — how far ahead a booking may start
- **Min booking duration** — the shortest booking allowed, in hours; 0 means no minimum
- **Max booking duration** — the longest booking allowed, in hours
- **Daily basis booking** — whether bookings cover whole days only
- **Don't restrict admins** — whether bookings administrators are exempt from the per-person limits, duration, advance, weekday and cancellation rules
- **Cancellation deadline** — whether a booking must be cancelled a minimum time before it starts
- **Max hours to cancel before start** — the minimum notice for cancelling while the cancellation deadline is on
- **Show bookers' names** — whether every User sees who booked a Space
- **Hide disallowed areas** — whether Areas a User may not book are hidden from them
- **Subject for bookings** — Disabled, Optional or Required; Disabled switches off every Space's subject requirement
- **Allow recurring bookings** — whether people may book a recurring series
- **Allow bookings for non-existing users** — whether a bookings administrator booking for an unknown email address creates that User
- **Default time zone** — the time zone of Areas without one of their own
- **Booking retention** — whether bookings that ended long ago are deleted
- **Retention days** — how many days after its end a booking is kept while booking retention is on
- **Disable buddies** — whether the buddies feature is switched off
- **Booking information emails for new users** — whether new Users start with booking information emails on
- **Enforce second factor** — Disabled, All users or Administrators only: who must set up an authenticator app or a passkey
- **Hide reports** — whether the presence report is withheld from everyone
- **Hide statistics** — whether the dashboard statistics are withheld from everyone
- **Target utilization** — the weekly hours per Space the utilization figures measure against
- **Kiosk mode** — whether Spaces may show their status on kiosk displays
- **Kiosk secret** — the secret a kiosk display presents; only whether one is set is ever shown
- **Public booking** — whether the public booking page is open
- **Public booking shows floor plan** — whether visitors pick a Space on the floor plan
- **Public booking shows availability** — whether Spaces already booked for the chosen slot are greyed out for visitors
- **Public booking min duration** — the shortest public booking, in hours
- **Public booking max duration** — the longest public booking, in hours
- **Allow any user** — whether a person unknown to the Organization who signs in through one of its identity providers gets a User
- **Groups feature** — whether the Organization's plan includes Groups, and with them approver groups
- **Recurring bookings feature** — whether the Organization's plan includes recurring bookings
- **Public booking feature** — whether the Organization's plan includes public booking
- **Kiosk mode feature** — whether the Organization's plan includes kiosk displays
- **Identity providers feature** — whether the Organization's plan includes identity providers
- **Unlimited users feature** — whether the Organization's plan lifts the limit of ten accounts
