# Project overview

## Name and purpose

**excalidraw-monorepo** is the upstream [Excalidraw](https://excalidraw.com) open-source codebase: a virtual hand-drawn style whiteboard with collaboration and end-to-end encryption in the hosted app. This repository contains:

- The **npm-distributable editor** (`@excalidraw/excalidraw` and related packages).
- The **reference web application** (`excalidraw-app`) that mirrors excalidraw.com-style features (PWA, collab, sharing).
- **Example integrations** under `examples/`.

## Executive summary

The codebase is a **Yarn workspaces monorepo**. The core drawing engine, scene model, and UI live primarily under `packages/excalidraw`. The `excalidraw-app` package is a Vite + React shell that composes the library with hosting-specific concerns (collaboration, Firebase, analytics hooks, etc.). Builds and tests are orchestrated from the repository root.

## Technology stack (summary)

| Category | Technology |
| --- | --- |
| Languages | TypeScript, SCSS |
| UI | React 19 |
| Bundler / dev server | Vite 5 |
| Package manager | Yarn 1.x workspaces |
| Tests | Vitest, ESLint, Prettier |
| App state (shell) | Jotai (excalidraw-app) |
| Editor state | Custom `actionManager` / `AppState` (see project architecture notes) |

## Repository structure type

**Monorepo** with clear separation between the **host application** (`excalidraw-app`) and **reusable packages** (`packages/*`).

## Documentation map

- [Master index](./index.md)
- [Architecture](./architecture.md)
- [Source tree](./source-tree-analysis.md)
- [Development guide](./development-guide.md)
- [Integration architecture](./integration-architecture.md)

## Related external documentation

Official contributor and user documentation lives at [docs.excalidraw.com](https://docs.excalidraw.com). This `docs/` folder is **project-local** documentation for AI and team context (BMad `project_knowledge`), not a replacement for the public docs site.
