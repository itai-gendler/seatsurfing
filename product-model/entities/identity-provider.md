---
domain: settings
relations:
- entity: provider-mapping
  verb: maps
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/router/auth-provider-router.go
- kind: code
  role: implementation
  target: server/repository/auth-provider-repository.go
---

# Identity provider

An OAuth 2 or OpenID Connect provider the Organization's people sign in through, with the user information fields Seatsurfing reads. Identity providers exist while the Organization's plan includes them.

## Information kept

- **Name** — the name shown on the sign-in page
- **Endpoints** — the provider's authorization, token and user information addresses and scopes
- **Client credentials** — the client ID and secret Seatsurfing presents; the secret is never shown again
- **User information fields** — which fields hold the email address, first name, last name and groups
- **Logout address** — where signing out also signs the person out of the provider
- **Profile page address** — where people manage their profile at the provider
- **Managed** — whether the provider is managed outside the Organization and cannot be changed or deleted there
