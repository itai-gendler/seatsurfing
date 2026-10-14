---
entities:
- entity: area
  shows:
  - Name
  - Description
  - Time zone
  - Enabled
  - Max bookings
  - Bookable weekdays
  - Floor plan
  - Allowed booker groups
  - Attribute values
  collects:
  - Name
  - Description
  - Time zone
  - Enabled
  - Max bookings
  - Bookable weekdays
  - Floor plan
  - Allowed booker groups
  - Attribute values
- entity: space
  shows:
  - Name
  - Position on floor plan
  - Enabled
  - Subject required
  - Public booking
  - Kiosk display
  - Approver groups
  - Allowed booker groups
  - Attribute values
  collects:
  - Name
  - Position on floor plan
  - Enabled
  - Subject required
  - Public booking
  - Kiosk display
  - Approver groups
  - Allowed booker groups
  - Attribute values
- entity: group
  shows:
  - Name
- entity: attribute
  shows:
  - Label
  - Type
entryPoints:
- web: /ui/admin/locations/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/admin/locations/[id].tsx
- kind: code
  role: implementation
  target: server/router/space-router.go#bulkUpdate
---

# Area editor

One Area with its settings, attribute values and floor plan and the Spaces drawn on it, each Space with its own settings, attribute values, approver groups and allowed booker groups.
