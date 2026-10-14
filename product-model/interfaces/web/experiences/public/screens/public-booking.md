---
entities:
- entity: organization
  shows:
  - Max days in advance
  - Public booking min duration
  - Public booking max duration
- entity: area
  shows:
  - Name
  - Floor plan
- entity: space
  shows:
  - Name
  - Position on floor plan
  - Subject required
- entity: booking
  collects:
  - Space
  - Enter
  - Leave
  - Subject
- entity: visitor
  collects:
  - Name
  - Email address
entryPoints:
- web: /ui/book/
references:
- kind: code
  role: implementation
  target: ui/src/pages/book/index.tsx
- kind: code
  role: implementation
  target: ui/src/pages/book/confirm/[id].tsx
---

# Public booking page

The Organization's public page where a visitor picks a day, a time slot and a Space opened for public booking, leaves their name and email address, and later lands again from the confirmation email to confirm the request.
