---
availability:
- place: web::booking-site
- place: web::administration
- place: rest-api
references:
- kind: code
  role: implementation
  target: server/router/booking-router.go#create
- kind: code
  role: implementation
  target: server/service/booking-service.go#PrepareCreate
- kind: code
  role: implementation
  target: server/service/booking-service.go#CommitCreate
- kind: code
  role: implementation
  target: server/service/booking-service.go#CheckBooking
- kind: code
  role: implementation
  target: server/router/recurring-booking-router.go#create
- kind: code
  role: implementation
  target: ui/src/pages/search.tsx
---

# Book a space

Reserve a Space for a time slot, once or as a recurring series. On the Booking Site a User books for themselves; in the administration a bookings administrator also books for someone else. The booking is confirmed at once, or waits for approval where the Space has approver groups, and every booking keeps to the Organization's booking rules, the Area's bookable weekdays and capacity, and the Space's allowed bookers.
