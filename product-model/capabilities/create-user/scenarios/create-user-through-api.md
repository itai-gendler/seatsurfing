---
kind: primary
routes:
  api: REST API
steps:
- text: The service account authenticates, is read-write and has Users access Admin
  kind: condition
  entities:
  - entity: service-account
    effect: reads
    facts:
    - Access mode
    - Users access
  - entity: user
    as: new-user
    effect: reads
    facts: []
  contexts:
    api:
      place: rest-api
- text: The service account sends the person's email address, names and how they sign in
  kind: actor
  actor: service-account
  entities: []
  contexts:
    api:
      place: rest-api
- text: The Product creates the User and emails an invitation when asked
  kind: product
  actor: service-account
  entities:
  - entity: user
    as: new-user
    effect: creates
    facts:
    - Email address
    - First name
    - Last name
    - Sign-in method
    - Identity provider
    - Password
    - Password change required
  contexts:
    api:
      place: rest-api
references:
- kind: spec
  role: intent
  target: specs/openapi.yaml
---

# Provision a user through the REST API

## Trigger

An integration adds a person to the Organization.

## Outcome

The User exists, invited, with a password or bound to an identity provider as the request says.
