---
appliesTo:
- type: capability
  id: book-space
- type: capability
  id: edit-booking
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#CheckBooking
- kind: code
  role: implementation
  target: server/service/space-service.go#IsUserAllowedToBookSpace
- kind: code
  role: implementation
  target: server/service/location-service.go#IsUserAllowedToBookLocation
---

# Only members of the allowed booker groups book a restricted Space or Area

Where a Space or its Area names allowed booker groups, only members of at least one of the Space's groups and one of the Area's groups book it; a Space and an Area without allowed booker groups are open to every User. Visitors' public requests are not restricted by allowed booker groups.
