---
kind: configuration
of: business-rule
settings:
- entity: organization
  fact: Don't restrict admins
takesEffect: Each time a booking is created, changed or cancelled. A settings change applies to the next such action.
stability: Bookings made earlier stay as they are when the setting changes.
alternatives:
- id: booking-limits-apply-to-everyone
  selectedWhen: Don't restrict admins is off. A missing setting counts as off.
- id: booking-limits-spare-bookings-administrators
  selectedWhen: Don't restrict admins is on.
references:
- kind: code
  role: implementation
  target: server/service/permissions.go#hasNoAdminRestrictions
---

# Booking limits for administrators

Organizations choose whether the people who manage bookings are held to the same per-person booking limits as everyone else; both policies are supported.
