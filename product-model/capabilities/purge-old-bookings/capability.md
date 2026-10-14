---
availability:
- place: web::administration
references:
- kind: code
  role: implementation
  target: server/repository/booking-repository.go#PurgeOldBookings
- kind: code
  role: implementation
  target: server/app/app.go#onTimerTick
---

# Purge old bookings

While the Organization keeps booking retention on, the Product deletes bookings that ended more than the retention days ago, oldest first.
