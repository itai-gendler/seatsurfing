---
availability:
- place: web::administration
- place: rest-api
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#GetFiltered
- kind: code
  role: implementation
  target: server/service/booking-service.go#GetCurrent
- kind: code
  role: implementation
  target: ui/src/pages/admin/bookings/index.tsx
---

# Browse bookings

Read the Organization's bookings for a period, filtered by Area and by person, in the administration or through the REST API, and download the list. It takes Bookings access Read.
