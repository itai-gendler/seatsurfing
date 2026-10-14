---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses one of the offered identity providers and signs in there
  kind: actor
  actor: user
  entities:
  - entity: identity-provider
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::public::sign-in
- text: No User has the reported address, the Organization allows any user and is within its user limit
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Allow any user
    - Unlimited users feature
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product creates the User bound to the provider and gives them the Roles and Group memberships the reported groups match
  kind: product
  actor: user
  entities:
  - entity: user
    effect: creates
    facts:
    - Email address
    - First name
    - Last name
    - Sign-in method
    - Identity provider
    - Roles
  - entity: provider-mapping
    effect: reads
    facts:
    - Group from provider
    - Target
  - entity: group
    effect: changes
    facts:
    - Members
  - entity: role
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product opens a session for the User and takes them to the Booking Site, or the administration when they came from there
  kind: product
  actor: user
  entities:
  - entity: session
    effect: creates
    facts:
    - Device
    - Created
  - entity: booking
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::sign-in
references:
- kind: code
  role: implementation
  target: server/router/auth-router.go#callback
---

# First sign-in of a new person through an identity provider

## Trigger

A person the Organization does not know yet signs in through one of its identity providers.

## Outcome

The person has a User bound to the provider, with the Roles and Groups its mappings grant, and is signed in.
