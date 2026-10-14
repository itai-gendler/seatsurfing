---
availability:
- place: web::booking-site
- place: web::administration
domain: preferences
references:
- kind: code
  role: implementation
  target: server/router/user-preferences-router.go#setAll
- kind: code
  role: implementation
  target: ui/src/pages/preferences.tsx
- kind: code
  role: implementation
  target: ui/src/pages/admin/approvals/index.tsx
---

# Change preferences

Change one's own preferences: booking defaults, booking information emails and reminders, email language, date and time format, preferred Area and floor plan colors. Approvers also switch their approval notifications on the Approvals page.
