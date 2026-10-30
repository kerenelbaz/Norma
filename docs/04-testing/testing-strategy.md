# Norma Testing Strategy

**Status:** Initial testing principles; detailed tooling to be selected during architecture design.

## Testing levels

- **Unit tests:** business rules, date/time handling, task logic, memory rules, permission decisions and provider adapters.
- **Integration tests:** API handlers, database operations, AI tool dispatch, calendar adapters and notification scheduling.
- **End-to-end tests:** user journeys across the mobile app and backend.
- **Manual device tests:** iOS permissions, EventKit behavior, push notifications, microphone, audio playback and app/deep-link handoff.
- **Failure tests:** offline behavior, timeouts, expired credentials, denied permissions, provider quota limits and duplicate/retried requests.

## Critical end-to-end journeys

1. Send a chat message and receive a response; conversation persists after restart.
2. Ask Norma to create a task; task appears in the Tasks UI.
3. Ask Norma to create an Apple Calendar event; permission and provider behavior are handled correctly.
4. Create a reminder and verify the supported notification path.
5. Add shopping items using text and later voice input.
6. Verify an automatically proposed memory, edit or delete it, and confirm retrieval behavior changes.
7. Open a destination in Google Maps or Waze through a supported deep link.

## Quality gates

A feature cannot be marked complete if critical tests fail, permissions are bypassed, secrets are exposed, data integrity is compromised or the user is told an action succeeded when it did not.
