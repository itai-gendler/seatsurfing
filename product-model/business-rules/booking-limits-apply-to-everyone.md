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
  target: server/service/booking-service.go#CheckBooking
---

# Booking limits apply to every User

Every booking a User makes, changes or cancels keeps to the number of upcoming bookings per person, the number of bookings a person holds at the same time, how far ahead a booking starts, the minimum and maximum duration, the Area's bookable weekdays and the cancellation deadline, whatever access the User has.
