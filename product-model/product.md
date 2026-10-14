---
id: seatsurfing
summary: Desk, seat and room booking for an organization's people, with areas and floor plans, recurring bookings, approver groups, roles and per-organization booking rules.
category: workplace-booking
tags:
- desk-booking
- room-booking
- hot-desking
license: GPL-3.0-only
languages:
- en
- de
- es
- et
- fi
- fr
- he
- hu
- it
- nl
- pl
- pt
- ro
- zh-TW
limitations:
- Every Area, Space, Group, Role and Booking belongs to exactly one Organization, and people book only within their own Organization.
- Every signed-in User can always book a Space for themselves, manage their own bookings, buddies and preferences and see the Areas they may book; roles only add administration on top of that baseline.
- A declined booking request is removed rather than kept as a declined record.
- Visitors without an account book only Spaces opened for public booking, and every such request waits for an approver.
- People may sign in through the Organization's own identity provider, which then decides their roles and Groups it maps; Seatsurfing keeps no password for them.
references:
- kind: doc
  role: intent
  target: README.md
- kind: spec
  role: context
  target: specs/custom-roles.md
- kind: code
  role: implementation
  target: server/service/booking-service.go
---

# Seatsurfing

Seatsurfing lets the people of an organization find and book desks, seats and rooms. Administrators lay out Areas with floor plans and the Spaces on them, decide which Groups may book where and which Groups approve bookings, define Roles that grant administrative access, and set the booking rules the whole Organization follows. People sign in with a password, a passkey or the organization's identity provider, book a free Space for a time slot or as a recurring series on the Booking Site, keep buddies and preferences, see and cancel their bookings, and approvers decide pending requests. Integrations work through the REST API with service accounts, rooms can show their status on a kiosk display, and organizations that open public booking let visitors without an account request a Space.

## Intent

Seatsurfing exists to enable an organization's employees to book seats, desks and rooms, as a self-hostable product or a hosted service, with a self-service booking site people can install on their phones and an administration area for the people who run the office.
