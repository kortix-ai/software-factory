---
name: dev-environment
description: "How to install, start and test this repository in a sandbox. Every factory agent loads it before it works."
---

# Dev environment

An example. Replace every command with the repository's own.

- Install: `pnpm install --frozen-lockfile`
- Start the app: `pnpm dev` (port 3000)
- Type check: `pnpm typecheck`
- Lint: `pnpm lint`
- Unit tests: `pnpm test`
- End-to-end tests: `pnpm test:e2e`

Services run locally and throwaway in the sandbox. Never point a command at a
shared staging or production backend.
