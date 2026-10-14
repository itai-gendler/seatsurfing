---
appliesTo:
- type: entity
  id: group
  effect: changes
  facts:
  - Members
  contexts:
  - place: web::public::sign-in
- type: entity
  id: user
  effect: changes
  facts:
  - Roles
  contexts:
  - place: web::public::sign-in
permits:
- actors:
  - user
references:
- kind: code
  role: implementation
  target: server/router/permissions.go#ReconcileUserFromIdP
---

# An identity provider's mappings set a person's Roles and Groups at their sign-in

When a person signs in through an identity provider, the Roles and Group memberships its mappings grant are replaced by those the reported groups match, without anyone's Roles or Groups access.
