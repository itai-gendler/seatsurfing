---
appliesTo:
- type: capability
  id: purge-old-bookings
- type: capability
  id: change-settings
references:
- kind: code
  role: implementation
  target: server/repository/booking-repository.go#PurgeOldBookings
- kind: code
  role: implementation
  target: server/router/settings-router.go#isValidSettingValue
---

# Retention never deletes a booking that ended less than 30 days ago

Booking retention keeps every booking for at least 30 days after it ends, whatever the retention days say; retention days lie between 30 and 999.
