---
kind: person
acts: external
relations:
- entity: booking
  verb: books
  cardinality: one-to-many
- entity: recurring-booking
  verb: books
  cardinality: one-to-many
- entity: passkey
  verb: registers
  cardinality: one-to-many
- entity: session
  verb: signs-in-with
  cardinality: one-to-many
- entity: buddy
  verb: keeps
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/service/permissions.go#GetEffectivePermissions
- kind: code
  role: implementation
  target: server/api/permissions.go
- kind: code
  role: implementation
  target: server/router/user-router.go
- kind: code
  role: implementation
  target: server/repository/user-preferences-repository.go
---

# User

A person of the Organization who books Spaces and, through the Roles they hold, may administer parts of it. Every signed-in User may book for themselves and manage their own account; each access level below is the highest one any of their Roles grants.

## Information kept

- **Email address** — the address the User signs in and receives email with
- **First name** — the User's first name
- **Last name** — the User's last name
- **Sign-in method** — Password, Invitation pending or Identity provider
- **Identity provider** — the identity provider the User signs in through, when that is their sign-in method
- **Password** — the User's password; never shown
- **Password change required** — whether the User must choose a new password at their next sign-in
- **Authenticator app** — whether an authenticator app gives the User a second factor
- **Has passkeys** — whether the User registered any passkey
- **Roles** — the Roles the User holds, assigned by hand or by an identity provider
- **Areas access** — None or Admin: whether the User administers Areas, floor plans, Spaces, approvers and allowed bookers
- **Space attributes access** — None or Admin: whether the User defines the attributes Spaces and Areas carry
- **Bookings access** — None, Read or Admin: Read sees every booking and its booker, Admin also books, changes and cancels for other people
- **Approvals access** — None, Write or Admin: Write decides bookings of Spaces whose approver groups include the User, Admin decides every pending booking
- **Analytics access** — None or Read: whether the User sees the dashboard statistics
- **Presence report access** — None or Read: whether the User sees who was present and when
- **Users access** — None, Read or Admin: Read sees the Organization's Users, Admin also creates, changes and deletes them
- **Groups access** — None, Read, Write or Admin: Write adds and removes members, Admin also creates, renames and deletes Groups
- **Roles access** — None, Read or Admin: Read sees Roles, Admin also defines them and assigns them to people
- **Service accounts access** — None or Admin: whether the User manages service accounts and their API tokens
- **Identity providers access** — None or Admin: whether the User manages the Organization's identity providers
- **Settings access** — None or Admin: whether the User changes the Organization's settings
- **Audit log access** — None or Read: whether the User sees the audit log of sign-in attempts
- **Booking information emails** — whether the User receives an email when one of their bookings is created, changed, approved, declined or cancelled
- **Booking reminders** — whether the User receives a reminder email about a day before a booking starts
- **Approval notifications** — whether the User receives an email when a booking they may approve is requested; off for new Users
- **Email language** — the language of the User's emails; the Organization's language when empty
- **Booking defaults** — when a new booking starts by default, the User's working hours, workdays and first day of the week
- **Preferred area** — the Area the Booking Site opens with
- **Date and time format** — how the User reads dates and times
- **Booking colors** — the colors the floor plan uses for free, booked, own, buddy's, partly booked and not allowed Spaces
- **CalDAV calendar** — the User's own CalDAV calendar that receives their bookings, when connected
