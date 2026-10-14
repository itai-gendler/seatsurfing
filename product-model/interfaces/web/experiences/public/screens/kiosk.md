---
entities:
- entity: space
  shows:
  - Name
- entity: area
  shows:
  - Name
- entity: booking
  shows:
  - Enter
  - Leave
  - Subject
  - Booker
entryPoints:
- web: /ui/kiosk/{id}/
references:
- kind: code
  role: implementation
  target: ui/src/pages/kiosk/[id].tsx
---

# Kiosk display

One Space's status for a screen beside it: free or occupied, the current and the next booking.
