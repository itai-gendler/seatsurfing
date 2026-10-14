---
appliesTo:
- type: capability
  id: book-space
- type: capability
  id: edit-booking
- type: capability
  id: request-public-booking
references:
- kind: code
  role: implementation
  target: server/repository/location-repository.go#AttachTimezoneInformation
---

# Booking times are read in the Area's time zone

Every booking's start and end are wall-clock times of its Area's time zone, or of the Organization's default time zone for an Area without one.
