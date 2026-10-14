---
entities:
- entity: user
  shows:
  - Booking defaults
  - Booking information emails
  - Booking reminders
  - Email language
  - Date and time format
  - Preferred area
  - Booking colors
  - Authenticator app
  - CalDAV calendar
  collects:
  - Booking defaults
  - Booking information emails
  - Booking reminders
  - Email language
  - Date and time format
  - Preferred area
  - Booking colors
  - Password
  - CalDAV calendar
- entity: passkey
  shows:
  - Name
  - Created
  - Last used
  collects:
  - Name
- entity: session
  shows:
  - Device
  - Created
entryPoints:
- web: /ui/preferences/
references:
- kind: code
  role: implementation
  target: ui/src/pages/preferences.tsx
- kind: code
  role: implementation
  target: ui/src/components/TotpSettings.tsx
- kind: code
  role: implementation
  target: ui/src/components/PasskeySettings.tsx
---

# Preferences

The User's own preferences: booking defaults, email notifications and language, formats, preferred Area and colors; their password, authenticator app, passkeys and active sessions; and their CalDAV calendar.
