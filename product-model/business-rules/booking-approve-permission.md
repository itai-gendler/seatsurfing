---
appliesTo:
- type: entity
  id: booking
  effect: changes
  to: Confirmed
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Approvals access
    is: Admin
- related:
  - verb: holds
    entity: space
  - verb: is-approved-by
    entity: group
  - verb: includes
    entity: user
  when:
  - entity: user
    fact: Approvals access
    is: Write
- actors:
  - user
  when:
  - entity: user
    fact: Approvals access
    is: Write
  - entity: space
    fact: Approver groups
    absent: true
- actors:
  - service-account
  when:
  - entity: service-account
    fact: Approvals access
    is: Admin
  - entity: service-account
    fact: Access mode
    is: Read-write
references:
- kind: code
  role: implementation
  target: server/service/booking-service.go#CanApproveBookingsInSpace
- kind: code
  role: implementation
  target: server/api/permissions.go
- kind: code
  role: implementation
  target: ui/i18n/translations.en-GB.json
---

# Approvers of the space, or approvals administrators, confirm a pending booking

A User with Approvals access Admin confirms any pending booking of the Organization. A User with Approvals access Write confirms a pending booking when they are a member of one of its Space's approver groups, or when the Space has no approver groups any more. A read-write service account with Approvals access Admin confirms any pending booking through the REST API.
