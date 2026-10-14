---
availability:
- place: web::booking-site
references:
- kind: code
  role: implementation
  target: server/app/app.go#sendBookingReminders
- kind: code
  role: implementation
  target: server/app/app.go#sendBookingReminderEmail
- kind: code
  role: implementation
  target: server/repository/booking-repository.go#GetBookingsDueForReminder
---

# Send booking reminder

Every five minutes the Product emails a reminder about a day before a confirmed booking starts to bookers who turned booking reminders on, unless they received another email about the booking in the last 24 hours.
