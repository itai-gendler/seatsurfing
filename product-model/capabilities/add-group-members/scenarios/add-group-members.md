---
kind: primary
routes:
  web: Web
steps:
- text: The User searches for Users and adds them to the Group
  kind: actor
  actor: user
  entities:
  - entity: user
    as: member
    effect: reads
    facts:
    - Email address
    - First name
    - Last name
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::group-editor
- text: The Product adds the Users to the Group's members
  kind: product
  actor: user
  entities:
  - entity: group
    effect: changes
    facts:
    - Members
  - entity: user
    as: member
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::group-editor
---

# Add members to a group

## Trigger

A User who manages Group membership puts people into a Group.

## Outcome

The Users are members and from now on book or approve wherever the Group is named.

## Edge cases

- Up to 64 Users are added at a time, and only Users of the Organization.
