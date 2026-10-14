---
entities:
- entity: buddy
  shows:
  - Colleague
  collects:
  - Colleague
- entity: booking
  shows:
  - Space
  - Enter
  - Leave
entryPoints:
- web: /ui/buddies/
references:
- kind: code
  role: implementation
  target: ui/src/pages/buddies.tsx
---

# My buddies

The User's buddies with each one's next booking, where buddies are added and removed.
