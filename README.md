# Norma

**Your Life, Organized.**

Norma is a personal AI secretary designed to manage everyday activities through natural-language text and voice. Its planned capabilities include calendar management, tasks, shopping lists, notes, reminders, personal memory, voice interaction and integrations with supported external applications.

## Product documentation

- [Product Requirements Document (PRD v1.0)](docs/01-product/PRD-v1.0.md)
- [Development Roadmap](docs/03-development/roadmap.md)
- [Scale 1 — Foundation](docs/03-development/scale-1.md)
- [Technical Architecture documentation plan](docs/02-architecture/README.md)
- [Testing Strategy](docs/04-testing/testing-strategy.md)

## Current direction

- Mobile: React Native + Expo + TypeScript.
- Backend: Cloudflare Workers (proposed).
- Database: Cloudflare D1 + Drizzle ORM (proposed).
- AI: provider-independent orchestration (provider not yet selected).
- Initial calendar support: Apple Calendar.
- Languages: Hebrew and English.
- Voice: push-to-talk first; continuous conversation later.
- Memory: automatic intelligent memory with user controls.
- Operating cost objective: target zero recurring cost; verify provider quotas and pricing before adoption.

See the PRD for requirements and open decisions. Proposed technology choices are not final until documented in an approved Architecture Decision Record.

## Repository layout

```text
Norma/
├── docs/
│   ├── 01-product/
│   ├── 02-architecture/
│   ├── 03-development/
│   └── 04-testing/
├── apps/
│   └── mobile/
├── packages/
├── infrastructure/
└── README.md
```

## Status

Product planning is underway. Technical Architecture and implementation have not started.
