---
appliesTo:
- type: entity
  id: organization
  effect: changes
  facts:
  - Groups feature
  - Recurring bookings feature
  - Public booking feature
  - Kiosk mode feature
  - Identity providers feature
  - Unlimited users feature
permits: []
references:
- kind: code
  role: implementation
  target: server/router/settings-router.go#isValidSettingNameWrite
- kind: code
  role: implementation
  target: server/app/app.go#InitializeSingleOrgSettings
---

# Nobody changes the plan features from the Organization's settings

Groups, recurring bookings, public booking, kiosk mode, identity providers and unlimited users are features of the Organization's plan. The settings page shows them and nobody changes them there; an installation holding a single Organization has them all.
