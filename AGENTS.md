# Agent guide

Instructions for AI coding agents working in this repository. **Start with the project knowledge index**, then drill into linked documents as needed.

## Primary entry point

- **[Project documentation index](docs/index.md)** — overview, quick reference, and links to all generated docs.

## Generated documentation (`docs/`)

| Topic | Document |
| --- | --- |
| Purpose, stack, monorepo shape | [docs/project-overview.md](docs/project-overview.md) |
| Layers, editor vs app, integrations, testing | [docs/architecture.md](docs/architecture.md) |
| Directory tree and entry points | [docs/source-tree-analysis.md](docs/source-tree-analysis.md) |
| High-level component areas | [docs/component-inventory.md](docs/component-inventory.md) |
| Install, scripts, tests, lint | [docs/development-guide.md](docs/development-guide.md) |
| CI/CD and Docker (overview) | [docs/deployment-guide.md](docs/deployment-guide.md) |
| Contributing and PR hygiene | [docs/contribution-guide.md](docs/contribution-guide.md) |
| App ↔ packages ↔ external SDKs | [docs/integration-architecture.md](docs/integration-architecture.md) |
| No in-repo REST; Firebase / Socket.io / Sentry notes | [docs/api-contracts-excalidraw-app.md](docs/api-contracts-excalidraw-app.md) |
| Client-side / scene JSON / storage (quick scan) | [docs/data-models-excalidraw-app.md](docs/data-models-excalidraw-app.md) |
| BMad scan metadata | [docs/project-scan-report.json](docs/project-scan-report.json) |

## Repository layout (short)

- **`excalidraw-app/`** — Vite + React host app (`yarn start` from repo root).
- **`packages/*`** — workspace libraries; core editor is `@excalidraw/excalidraw`.
- **`examples/*`** — integration samples.

## Cursor rules (must follow)

Each rule includes a **How to verify** section. Apply the rules that match the files you touch.

| Rule | File |
| --- | --- |
| Protected core files | [.cursor/rules/do-not-touch.mdc](.cursor/rules/do-not-touch.mdc) |
| Editor architecture (state, canvas, deps) | [.cursor/rules/architecture.mdc](.cursor/rules/architecture.mdc) |
| TS/React conventions in `packages/` | [.cursor/rules/conventions.mdc](.cursor/rules/conventions.mdc) |
| Vitest, snapshots, coverage | [.cursor/rules/testing-vitest.mdc](.cursor/rules/testing-vitest.mdc) |
| Host app (`excalidraw-app`), Jotai, Vite | [.cursor/rules/excalidraw-app.mdc](.cursor/rules/excalidraw-app.mdc) |
| Yarn workspaces and builds | [.cursor/rules/monorepo-workspaces.mdc](.cursor/rules/monorepo-workspaces.mdc) |
| ESLint import order and package-internal imports | [.cursor/rules/imports-eslint.mdc](.cursor/rules/imports-eslint.mdc) |
| PR / CI quality gate (Node 20, `yarn test:all`) | [.cursor/rules/ci-and-pr.mdc](.cursor/rules/ci-and-pr.mdc) |

## Cursor slash commands

Custom prompts live in [`.cursor/commands/`](.cursor/commands/):

- **`/create-component`** — [create-component.md](.cursor/commands/create-component.md): scaffold a React component per repo conventions (props type, named exports, tests, ESLint/Jotai rules).
- **`/install-validate-run`** — [install-validate-run.md](.cursor/commands/install-validate-run.md): `yarn install` → `yarn test:all` → `yarn start` (dev server in background; stop if validation fails).

## Quick commands

From the repo root (details in [docs/development-guide.md](docs/development-guide.md)):

- `yarn` — install
- `yarn start` — dev server (app)
- `yarn test:all` — typecheck, lint, format check, tests

## Official upstream docs

For product behavior, public API, and contributor process outside this repo’s `docs/`:

- [Excalidraw documentation](https://docs.excalidraw.com)
- [Development](https://docs.excalidraw.com/docs/introduction/development)
- [Contributing](https://docs.excalidraw.com/docs/introduction/contributing)

## Documentation scope

The files under `docs/` were produced by a **quick** brownfield scan. Deep behavior (collab protocols, Firebase usage, full data shapes) may require reading source under `excalidraw-app/collab/`, `excalidraw-app/data/`, and `packages/excalidraw/` directly.
