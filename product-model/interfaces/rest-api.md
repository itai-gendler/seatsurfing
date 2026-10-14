---
type: api
actors:
- service-account
references:
- kind: spec
  role: intent
  target: specs/openapi.yaml
- kind: spec
  role: intent
  target: specs/service-account-bearer-auth.md
- kind: code
  role: implementation
  target: server/router/routes.go#VerifyAuthMiddleware
---

# Seatsurfing REST API

The documented REST API integrations use with a service account, authenticating with its username and password or an API token. A service account reaches what its Roles grant, and a read-only service account only reads.

## Intent

Let other systems book, cancel and decide bookings, read the Organization's bookings and provision people without going through the browser.
