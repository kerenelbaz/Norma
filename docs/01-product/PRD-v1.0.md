# NORMA — Product Requirements Document

**Version:** 1.0  
**Status:** Product baseline — ready for architecture design  
**Last updated:** 2026-10-30  
**Product tagline:** Your Life, Organized.

## 1. Executive summary

Norma is a personal AI secretary for one individual. It combines conversational AI, personal organization, calendar management, reminders, voice interaction, personal memory and integrations with external applications.

The user can communicate with Norma through text or voice. Norma interprets requests, identifies the required operation, invokes validated application services, and reports the outcome. Norma is intended to do more than answer questions: it should carry out authorized tasks on the user's behalf.

**Product principle: One assistant, one memory, multiple capabilities.**

## 2. Vision and objectives

Norma should help the user organize everyday life through one coherent assistant that:

- Understands natural language in Hebrew and English.
- Remembers useful, relevant information across conversations.
- Manages calendars, tasks, shopping lists, notes and reminders.
- Communicates proactively through notifications when authorized.
- Accepts voice requests and responds with speech.
- Opens or interacts with supported external applications.
- Connects information across modules to provide useful context and suggestions.
- Operates with a target of zero recurring infrastructure and AI costs, subject to provider limits and platform requirements.

## 3. Target user and product scope

The initial product is a single-user personal application, primarily for iPhone. Android support should remain possible without redesigning the backend. Multi-user collaboration, public registration, enterprise administration and payment features are out of scope for the initial release.

## 4. Product principles

1. **Mobile first:** The primary experience is an iPhone application.
2. **Conversational and visual:** Every core capability should be accessible through chat and through a dedicated UI where appropriate.
3. **Modular:** Calendar, tasks, reminders, memory, voice and integrations are independent capabilities.
4. **One coherent assistant:** Modules share authorized context through the AI orchestration layer.
5. **Safe execution:** AI proposes tool actions; backend services validate and execute them. The AI never writes directly to the database.
6. **User control:** The user can inspect and manage memory, permissions, integrations and notification preferences.
7. **Cost-aware:** Prefer open-source software and free tiers; verify current quotas and pricing before adopting a provider.

## 5. Functional requirements

Priority definitions: **Critical** = required for a useful core product; **High** = important planned capability; **Medium** = later capability.

### 5.1 AI assistant — Critical

- AI-001: Accept natural-language text messages.
- AI-002: Understand user intent and relevant context.
- AI-003: Maintain context within a conversation.
- AI-004: Persist conversation history.
- AI-005: Identify when a request requires an application action.
- AI-006: Invoke backend tools through a controlled tool/function-calling interface.
- AI-007: Support multi-step requests and report each relevant outcome.
- AI-008: Ask clarifying questions when required information is missing or ambiguous.
- AI-009: Confirm successful actions and clearly report failures.
- AI-010: Support Hebrew and English input and output.
- AI-011: Use structured outputs for operations that require predictable data.
- AI-012: Avoid claiming an action succeeded until the backend confirms success.

### 5.2 Automatic personal memory — High

- MEM-001: Identify potentially useful long-term facts and preferences from conversations.
- MEM-002: Save appropriate memories automatically, subject to privacy and sensitivity rules.
- MEM-003: Distinguish temporary conversation context from persistent memory.
- MEM-004: Retrieve relevant memories when answering or planning.
- MEM-005: Associate memories with categories, timestamps and provenance where practical.
- MEM-006: Allow the user to inspect, correct and delete saved memories.
- MEM-007: Avoid saving sensitive information without appropriate explicit consent.
- MEM-008: Do not convert uncertain AI inferences into established facts.
- MEM-009: Provide a way to disable automatic memory or adjust what may be remembered.

### 5.3 Calendar management — Critical

**Initial requirement: support Apple Calendar from the beginning.** Google Calendar is a planned additional provider, not a prerequisite for the first calendar release.

- CAL-001: View daily, weekly and monthly events.
- CAL-002: Retrieve upcoming events and search by date, title or category.
- CAL-003: Create, edit and delete events.
- CAL-004: Support recurring events where the provider API permits.
- CAL-005: Identify scheduling conflicts.
- CAL-006: Find available time slots where sufficient calendar data is accessible.
- CAL-007: Set event-related reminders where supported.
- CAL-008: Support natural-language calendar operations.
- CAL-009: Handle calendar permissions, denied access and revoked access gracefully.
- CAL-010: Clearly communicate sync state and provider limitations.
- CAL-011: Design a provider abstraction so Google Calendar can be added without rewriting calendar business logic.

**Platform note:** On iOS, EventKit can access calendars available to the device with user permission. This is not automatically equivalent to server-side iCloud access. Remote synchronization, background behavior and Android support require explicit architecture decisions.

### 5.4 Tasks and To-Do lists — Critical

- TASK-001: Create, edit, delete and complete tasks.
- TASK-002: Set priority, due date, category and status.
- TASK-003: Support subtasks.
- TASK-004: Support recurring tasks where appropriate.
- TASK-005: Display pending, completed and overdue tasks.
- TASK-006: Filter and sort tasks.
- TASK-007: Create and update tasks through natural-language conversation.

### 5.5 Shopping lists — High

- SHOP-001: Create and manage multiple lists.
- SHOP-002: Add, edit and remove items.
- SHOP-003: Store optional quantity, unit and category.
- SHOP-004: Mark items as purchased.
- SHOP-005: Retrieve and update lists through conversation.

### 5.6 Notes — Medium

- NOTE-001: Create, edit and delete notes.
- NOTE-002: Categorize and search notes.
- NOTE-003: Retrieve relevant notes through conversation.
- NOTE-004: Save conversational information as a note when requested.

### 5.7 Reminders and notifications — Critical

- NOT-001: Create one-time and recurring reminders.
- NOT-002: Associate reminders with tasks and calendar events.
- NOT-003: Deliver push notifications with user permission.
- NOT-004: Allow reminders to be postponed, completed or dismissed.
- NOT-005: Provide notification preferences and quiet hours.
- NOT-006: Support morning briefings and evening summaries.
- NOT-007: Notify about overdue tasks when configured.
- NOT-008: Handle time zones and daylight-saving changes correctly.
- NOT-009: Prevent duplicate delivery and record delivery status where possible.
- NOT-010: Make clear that remote notifications require a reachable backend and a configured push provider; local notifications may have different behavior.

### 5.8 Voice assistant — High

**Agreed rollout:** push-to-talk first; continuous conversational voice later.

- VOICE-001: Capture voice input after an explicit user action.
- VOICE-002: Convert speech to text.
- VOICE-003: Process recognized speech through the same AI and tool system as text.
- VOICE-004: Convert responses to speech.
- VOICE-005: Support Hebrew and English subject to selected speech providers.
- VOICE-006: Provide spoken action confirmations.
- VOICE-007: Allow the user to stop or interrupt playback.
- VOICE-008: Provide a clear recording/listening indicator and permission handling.
- VOICE-009: Design for a later continuous voice session without assuming always-on background listening is permitted by iOS.

### 5.9 External integrations — High / staged

- INT-001: Apple Calendar — initial calendar provider through native iOS capabilities and permissions.
- INT-002: Google Calendar — additional provider in a later integration increment.
- INT-003: Spotify — open the app or a playlist/track; add supported playback controls subject to Spotify API, account and device restrictions.
- INT-004: Google Maps — open directions or navigation using supported URL/deep-link flows.
- INT-005: Waze — open navigation using supported deep links.
- INT-006: Apple Shortcuts — trigger user-configured shortcuts where supported by the chosen app/native integration.
- INT-007: Gmail — future ability to search/read/summarize and draft messages; sending requires explicit authorization.
- INT-008: Keep integrations modular, permission-scoped and independently configurable.

### 5.10 Intelligence and automation — Future

- AUTO-001: Detect calendar conflicts.
- AUTO-002: Suggest time slots for unfinished tasks.
- AUTO-003: Estimate travel time and suggest departure reminders when location and routing data are available.
- AUTO-004: Identify overdue or neglected tasks.
- AUTO-005: Generate contextual daily briefings.
- AUTO-006: Suggest routines and automations based on repeated behavior, with user control.
- AUTO-007: Respect configured autonomy and confirmation rules.

### 5.11 Future modules — Not initial-release commitments

Expense tracking, travel planning, document management, habit tracking, meal planning, subscription tracking, birthday management and home maintenance may be considered after the core product is stable.

## 6. User experience and navigation

The application should be modern, accessible, mobile-first and optimized for iPhone.

Proposed main areas:

- **Home:** greeting, daily briefing, upcoming events, priority tasks and quick actions.
- **Assistant:** chat history, text input, microphone and action confirmations.
- **Calendar:** calendar views and event management.
- **Tasks:** tasks, To-Do lists and shopping lists.
- **Memory:** inspect and manage remembered information.
- **Settings:** language, notifications, AI provider, integrations, permissions and privacy controls.

The same core operations should be available through conversation and dedicated screens. UI state should reflect successful backend changes.

## 7. Autonomy and permissions

**Proposed default: Level 2.** Norma may perform routine, reversible organization actions independently, while asking before sensitive, consequential or irreversible actions.

Examples of routine actions: adding a shopping item, creating an ordinary task, retrieving events, saving a non-sensitive note or creating a reminder.

Examples requiring confirmation: sending an email, making a purchase, sharing personal information, deleting important events or performing financial/irreversible actions.

The user must be able to review and change permissions. Each tool must enforce authorization server-side; the AI's statement that an action is permitted is not sufficient.

## 8. Non-functional requirements

### Performance
- Keep interactions responsive and avoid blocking the UI during network operations.
- Show loading, success and failure states.
- Use efficient API calls and pagination where needed.

### Reliability
- Prevent duplicate execution for retried actions where feasible.
- Handle network failures and expired credentials.
- Persist data safely and report synchronization status.
- Make scheduled reminders resilient to application closure and device restarts, within platform capabilities.

### Security and privacy
- Secure authentication and protected backend endpoints.
- Store integration credentials securely; never expose secrets in the mobile bundle.
- Use least-privilege provider scopes.
- Encrypt sensitive credentials at rest where supported.
- Maintain an activity log for important actions.
- Provide memory review and deletion controls.
- Minimize data shared with AI and external providers.

### Accessibility and localization
- Support Hebrew and English.
- Support right-to-left layouts for Hebrew.
- Respect device text scaling and accessibility settings.
- Handle locale, time zone and date formats explicitly.

### Maintainability
- Use modular services and typed contracts.
- Keep AI provider and integration adapters replaceable.
- Document architecture decisions and migrations.
- Test business logic independently from UI and AI provider behavior.

## 9. Technical direction (not a complete architecture)

- **Mobile:** React Native + Expo + TypeScript.
- **Navigation:** Expo Router (proposed).
- **Backend:** Cloudflare Workers + TypeScript (proposed).
- **Database:** Cloudflare D1 with Drizzle ORM (proposed).
- **AI:** provider-independent orchestration and tool calling; free-tier cloud or local models may be evaluated.
- **Notifications:** Expo Notifications and a compatible push delivery path, subject to provider and platform constraints.
- **Source control:** GitHub.

The detailed service boundaries, authentication, synchronization approach, schema, APIs, secrets, deployment and provider choices belong in the Technical Architecture document.

## 10. Cost objective

Target zero recurring monthly cost for personal use. Prefer free tiers and open-source tools. Before selecting any service, verify current pricing, quotas, commercial/personal-use terms and limitations. The product must degrade gracefully if a free quota is reached. Do not introduce paid dependencies without explicit user approval.

## 11. Development scales and deliverables

### Scale 1 — Foundation
Project setup, Expo app, navigation, design system, authentication, backend, database, AI provider abstraction, chat, conversation persistence and initial memory.

**Deliverable:** deployed, usable AI assistant with persistent conversations and controlled memory.

### Scale 2 — Personal Organization
Apple Calendar integration, tasks, To-Do lists, shopping lists, notes and AI tool actions.

**Deliverable:** daily organization managed through both UI and conversation.

### Scale 3 — Reminders and Notifications
Reminder engine, scheduling, push delivery, recurring reminders, morning briefing and evening summary.

**Deliverable:** proactive notifications that work within iOS and backend constraints.

### Scale 4 — Voice Assistant
Push-to-talk, speech recognition, spoken responses, Hebrew/English support and later continuous voice sessions.

**Deliverable:** voice-based interaction using the same action system as text.

### Scale 5 — External Integrations
Spotify, Google Maps, Waze, Apple Shortcuts, Google Calendar and Gmail in separately scoped increments.

**Deliverable:** Norma can invoke supported external application actions with appropriate permissions.

### Scale 6 — Intelligence and Automation
Context awareness, smart scheduling, suggestions, conflict detection, travel-aware reminders and user-approved routines.

**Deliverable:** proactive assistance based on connected data.

### Scale 7 — Advanced Personal Assistant
Evaluate and add expense, travel, document, habit, meal and subscription modules.

**Deliverable:** expanded personal assistant capabilities.

## 12. Initial data domains

Expected domains include user preferences, conversations, messages, memories, calendar connections, calendar references/events, tasks, categories, shopping lists/items, notes, reminders, notification deliveries, integrations/credentials and action logs.

This is a conceptual inventory, not a finalized database schema. The Technical Architecture must define ownership, relationships, retention, indexes, provider identifiers and synchronization behavior.

## 13. Testing and acceptance

Every feature must have appropriate unit, integration and end-to-end tests. Critical workflows include:

- Create an event through chat and verify it appears in the authorized calendar.
- Retrieve events for a requested date.
- Create a task and reminder through natural language.
- Receive a scheduled notification without relying on the app remaining open, within supported platform behavior.
- Add multiple shopping items through voice.
- Retrieve and correct a saved memory.
- Open navigation in the selected supported app.
- Handle denied permissions, offline state, expired tokens and provider failures.

A scale is complete only when its agreed acceptance criteria pass and the deployed functionality is verified.

## 14. Out of scope for the initial release

- Multi-user collaboration and public registration.
- Enterprise administration.
- Subscription or payment processing.
- Autonomous financial transactions.
- Unrestricted control of third-party apps.
- Always-on background listening.

## 15. Open decisions to resolve in Technical Architecture

1. Exact Apple Calendar strategy: EventKit-only device access, iCloud CalDAV/server sync, or a staged combination.
2. Whether a companion web interface is needed in addition to the native app.
3. Authentication approach for a single-user deployment.
4. AI provider(s), model selection, quota handling and local fallback feasibility.
5. Speech-to-text and text-to-speech providers and cost limits.
6. Push notification delivery architecture and scheduling reliability.
7. Secure credential storage and token refresh strategy.
8. Backup, export, retention and disaster recovery.
9. Whether Cloudflare D1 and Workers free-tier constraints fit all expected workloads.
10. Native Expo modules and any required development build or config plugins.

## 16. Definition of done

A feature is complete when requirements are implemented, UI and backend behavior are verified, data persists correctly, authorization is enforced, failure states are handled, tests pass, documentation is updated and the feature is deployed and verified.

## 17. Product statement

Norma should evolve from a conversational AI assistant into a reliable personal secretary that understands the user's everyday life, organizes activities, performs authorized actions, communicates naturally and proactively helps the user stay organized.

**NORMA — Your Life, Organized.**
