---
availability:
- place: web::booking-site
- place: web::administration
- place: web::public
- place: rest-api
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#DeleteBooking
- kind: code
  role: implementation
  target: server/router/recurring-booking-router.go#delete
- kind: code
  role: implementation
  target: server/router/public-booking-router.go#deleteBooking
- kind: code
  role: implementation
  target: ui/src/pages/bookings.tsx
---

# Cancel booking

Cancel a booking before it ends: a User cancels their own booking, or all upcoming bookings of their series, from the Booking Site; a bookings administrator deletes anyone's booking in the administration; a visitor cancels their approved booking from the link in the approval email. The Organization's cancellation deadline applies.
