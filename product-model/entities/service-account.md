---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: server/router/routes.go#VerifyAuthMiddleware
- kind: code
  role: implementation
  target: server/router/user-router.go#generateApiToken
- kind: spec
  role: intent
  target: specs/service-account-bearer-auth.md
---

# Service account

A non-person account an integration uses to call the REST API with a username and password or an API token. Its Roles grant its access like a User's, and a read-only service account only reads.

## Information kept

- **Name** — the name the service account is listed under
- **Username** — the name it authenticates with
- **Access mode** — Read-only or Read-write
- **API token** — whether a long-lived API token is configured; the token itself is shown once
- **Password** — the service account's password; never shown
- **Areas access** — None or Admin, as for a User
- **Bookings access** — None, Read or Admin, as for a User
- **Approvals access** — None, Write or Admin, as for a User
- **Users access** — None, Read or Admin, as for a User
