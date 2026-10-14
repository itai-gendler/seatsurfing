---
kind: primary
routes:
  web: Web
steps:
- text: The User enters their email address
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Email address
  contexts:
    web:
      place: web::public::sign-in
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
- text: The provider reports an email address of a User bound to this provider, or of nobody while the Organization allows any user
  kind: condition
  entities:
  - entity: organization
    effect: reads
    facts:
    - Allow any user
  - entity: user
    effect: reads
    facts:
    - Identity provider
  contexts:
    web:
      place: web::public::sign-in
- text: The Product takes the User's names from the provider and replaces the Roles and Group memberships its mappings grant with those the reported groups match
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - First name
    - Last name
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
- kind: code
  role: implementation
  target: server/router/permissions.go#ReconcileUserFromIdP
---

# Sign in through an identity provider

## Trigger

A User whose Organization uses an identity provider signs in.

## Outcome

The User is signed in; their names and the Roles and Group memberships the provider maps follow what the provider reports.

## Edge cases

- Roles and Group memberships an administrator assigned by hand stay.
- A change that would leave the Organization without an administrator keeps the User's Roles as they are.
- An address the Organization does not know is refused while the Organization does not allow any user.
