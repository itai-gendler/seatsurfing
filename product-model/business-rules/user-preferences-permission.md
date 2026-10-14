---
appliesTo:
- type: entity
  id: user
  effect: changes
  facts:
  - Booking defaults
  - Booking information emails
  - Booking reminders
  - Approval notifications
  - Email language
  - Date and time format
  - Preferred area
  - Booking colors
  - CalDAV calendar
permits:
- self: true
references:
- kind: code
  role: implementation
  target: server/router/user-preferences-router.go#setAll
---

# Only the person changes their own preferences

A User's booking defaults, notifications, language, formats, preferred Area, colors and calendar connection are changed by that User alone.
