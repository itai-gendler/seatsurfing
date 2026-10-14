---
appliesTo:
- type: capability
  id: book-space
- type: capability
  id: edit-booking
- type: capability
  id: cancel-booking
references:
- kind: code
  role: implementation
  target: server/service/permissions.go#hasNoAdminRestrictions
- kind: code
  role: implementation
  target: server/service/booking-service.go#IsValidBookingAdvance
- kind: code
  role: implementation
  target: server/service/location-service.go#IsLocationWeekdayBookable
---

# Booking limits spare bookings administrators

A User with Bookings access Admin is exempt from the number of upcoming bookings per person, the number of bookings a person holds at the same time, how far ahead a booking starts, the minimum and maximum duration, the Area's bookable weekdays and the cancellation deadline; a booking still may not end in the past or start before today, and the Area's capacity and the slot check apply to everyone.
