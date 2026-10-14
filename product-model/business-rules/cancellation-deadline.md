---
appliesTo:
- type: capability
  id: cancel-booking
  contexts:
  - place: web::booking-site
  - place: web::administration
  - place: web::public
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#DeleteBooking
- kind: code
  role: implementation
  target: server/service/booking-service.go#IsValidBookingHoursBeforeDelete
---

# A booking is cancelled before it ends and, with a deadline, early enough

A booking whose end is before today is never cancelled. While the Organization sets a cancellation deadline, a booking is cancelled at least Max hours to cancel before start hours before it starts.
