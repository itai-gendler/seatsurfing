---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User enters the new Group's name and saves
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::administration::group-editor
  capability: create-group
- text: The Product creates the Group and opens it in the group editor
  kind: product
  actor: user
  entities:
  - entity: group
    effect: creates
    facts:
    - Name
    - Members
  contexts:
    web:
      place: web::administration::group-editor
  capability: create-group
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
    facts:
    - Name
  contexts:
    web:
      place: web::administration::group-editor
  capability: add-group-members
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
  capability: add-group-members
---

# Create a group and add its members

## Trigger

A Groups administrator needs a new Group for an Area's or Space's approvers or allowed bookers.

## Outcome

The Group exists with its first members.
