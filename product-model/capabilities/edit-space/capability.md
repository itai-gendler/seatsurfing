---
availability:
- place: web::administration
domain: areas
references:
- kind: code
  role: implementation
  target: server/router/space-router.go#update
- kind: code
  role: implementation
  target: server/router/space-router.go#bulkUpdate
---

# Edit space

Change a Space's name, position, attribute values, whether it is enabled, whether it requires a subject, whether it shows on a kiosk display and whether it is open to public booking.
