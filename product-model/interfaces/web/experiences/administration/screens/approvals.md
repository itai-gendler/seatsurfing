---
entities:
- entity: booking
  shows:
  - Booker
  - Space
  - Enter
  - Leave
  - Subject
  - Public request
- entity: area
  shows:
  - Name
- entity: user
  shows:
  - Approval notifications
  collects:
  - Approval notifications
entryPoints:
- web: /ui/admin/approvals/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/approvals/index.tsx
- kind: code
  role: implementation
  target: server/service/booking-service.go#GetPendingApprovals
---

# Approvals

The pending bookings the User may decide, earliest start first, each approved or declined from here, with the User's own approval notifications switch.
