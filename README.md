# Noxa's Dev Team

A Claude Code plugin that spawns **9 senior specialist personas** to review your code — together as a coordinated team or individually as focused solo reviewers.

Built for Claude Code. Ships as an installable plugin.

## The Team

| # | Name | Role | Strength |
|---|------|------|---------|
| 1 | **Bryl** | Senior PM / Team Lead | Scope, risk, unified synthesis |
| 2 | **Jazelei** | Senior Frontend Engineer | React, TypeScript, Tailwind, a11y, UI quality |
| 3 | **Omhar** | Senior Backend Engineer | APIs, Postgres/Supabase, system design, caching |
| 4 | **Custodio** | Senior Security Engineer | OWASP Top 10, auth, data protection, DDoS layers |
| 5 | **Franco** | Senior QA Engineer | Testing, edge cases, coverage |
| 6 | **Manny** | Senior Product Manager | UX flows, feature completeness, business value |
| 7 | **Gab** | Senior DevOps Engineer | CI/CD, Docker, deployment, monitoring |
| 8 | **Gemini** | Senior UI/UX Designer | Visual polish, design system, world-class aesthetics |
| 9 | **Android** | Senior Mobile Engineer | React Native, PWA, mobile UX/performance |

## Install

```sh
/plugin marketplace add OmharRegidor/noxadevteam
/plugin install noxadevteam@omhar
```

## Usage

### Team review (coordinated multi-agent)

```
/noxadevteam
/noxadevteam src/pages/CheckoutPage.tsx
/noxadevteam the new auth middleware
```

Bryl picks only the relevant specialists for the change, spawns them in parallel, then synthesizes a unified P0–P3 prioritized review with a ship/no-ship call.

### Solo review (any single specialist)

```
/jazelei src/components/Header.tsx
/omhar supabase/migrations/2026_user_tokens.sql
/custodio the login flow
/franco tests/auth.spec.ts
/gemini src/pages/HomePage.tsx
/gab .github/workflows/deploy.yml
/manny the new onboarding feature
/android src/mobile/
/bryl the release readiness
```

Each solo command runs just that specialist against the target and reports findings concisely.

## How it works

- The team command (`/noxadevteam`) selects relevant agents based on what changed, spawns them in parallel via the Agent tool (using Sonnet for teammates to save tokens), then Bryl synthesizes a unified review.
- Each specialist has a detailed persona file under `commands/agents/` describing their traits, focus areas, key actions, boundaries, and deliverables.
- Solo commands (`/jazelei`, `/omhar`, etc.) load the same persona file for a focused one-agent review.

## Structure

```
.claude-plugin/
  plugin.json           # Plugin manifest
  marketplace.json      # Single-plugin marketplace (for /plugin install)
commands/
  noxadevteam.md        # Team coordinator
  {name}.md             # Solo-review wrapper for each specialist
  agents/
    {name}.md           # Full persona definition for each specialist
```

## License

MIT © Omhar Regidor
