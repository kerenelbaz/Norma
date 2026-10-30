# Scale 1 — Foundation

**Status:** Not started. This document will be expanded after Technical Architecture approval.

## Objective

Deliver a deployed, usable Norma mobile application with authentication, an AI chat experience, persistent conversations and an initial user-controlled automatic memory capability.

## Planned workstreams

1. Repository and workspace setup.
2. Expo / React Native application bootstrap.
3. Navigation and responsive mobile UI foundation.
4. Design tokens and reusable components.
5. Authentication and single-user access control.
6. Cloudflare Worker API and environment configuration.
7. D1 database and Drizzle migrations.
8. AI provider abstraction and secure server-side model invocation.
9. Chat, conversation history and message persistence.
10. Initial memory extraction, retrieval, review and deletion controls.
11. Logging, error handling and automated tests.
12. Deployment and operational documentation.

## Acceptance criteria — draft

- The app installs and launches on the target iPhone.
- An unauthenticated user cannot access private data or API operations.
- The user can send a text message and receive an AI response.
- Conversations and messages persist across app restarts.
- AI tool requests cannot bypass backend validation.
- Candidate memories follow the agreed privacy rules and can be reviewed, corrected and deleted.
- Secrets are not embedded in the mobile application.
- Core flows have automated tests and are verified in a deployed environment.

Detailed tasks, architecture dependencies and measurable performance targets are pending Technical Architecture approval.
