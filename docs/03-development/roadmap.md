# Norma Development Roadmap

**Version:** 1.0  
**Status:** Initial roadmap aligned with PRD v1.0

## Delivery approach

Develop Norma incrementally. Each scale must have scoped requirements, technical design, implementation tasks, tests and acceptance criteria. Do not begin the next scale until the current scale's agreed acceptance criteria are met or explicitly deferred.

## Scales

| Scale | Scope | Exit deliverable |
|---|---|---|
| 1 — Foundation | Expo app, navigation, design system, authentication, backend, database, AI adapter, chat, conversation persistence, initial memory | Usable deployed AI assistant |
| 2 — Personal Organization | Apple Calendar, tasks, To-Do, shopping lists, notes, AI tools | Organization modules usable through UI and chat |
| 3 — Reminders & Notifications | One-time/recurring reminders, push delivery, briefings, overdue notifications | Proactive notification workflows |
| 4 — Voice Assistant | Push-to-talk, speech-to-text, text-to-speech, Hebrew/English, later continuous sessions | Voice requests and spoken responses |
| 5 — External Integrations | Spotify, Google Maps, Waze, Apple Shortcuts, Google Calendar, Gmail | Independently permissioned integrations |
| 6 — Intelligence & Automation | Contextual planning, conflict detection, travel-aware reminders, suggestions, routines | Context-aware proactive assistant |
| 7 — Advanced Assistant | Expenses, travel, documents, habits, meals, subscriptions and other modules | Expanded personal assistant |

## Working method for every scale

1. Confirm scope and user stories.
2. Review dependencies and risks.
3. Update architecture and decision records.
4. Define data/API/UI changes.
5. Break work into small implementation issues.
6. Implement on feature branches.
7. Add automated tests and manual verification steps.
8. Review, merge and deploy.
9. Update documentation and mark acceptance criteria.

## Initial priority

Start with Scale 1 only after the Technical Architecture and Scale 1 specification are approved. Avoid implementing future-scale features prematurely, but preserve extension points where they are inexpensive and justified.
