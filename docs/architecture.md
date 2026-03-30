# Architecture

## Executive summary

Excalidraw is a **browser-based canvas editor** packaged as reusable libraries plus a **reference application**. Rendering uses **Canvas 2D**, not React DOM, for the drawing surface. Application state in the core editor is driven by a **custom action system** (`actionManager`); the host app may use additional libraries (e.g. Jotai) for shell-level concerns.

## Technology stack

- **Languages:** TypeScript, SCSS
- **UI framework:** React 19
- **Build:** Vite 5, Yarn workspaces
- **Testing:** Vitest, ESLint, Prettier

## Architecture pattern

- **Monorepo:** workspace packages with a clear dependency direction: `excalidraw-app` → `@excalidraw/excalidraw` (+ sibling packages as needed).
- **Editor core:** Component and module layout under `packages/excalidraw` with separation between scene data, actions, UI chrome, and render pipeline.
- **Host app:** `excalidraw-app` adds product features (collaboration, storage backends, error reporting) around the embedded editor.

## Data and persistence

- **Scene documents** are JSON-serializable (`.excalidraw` export); in-app persistence uses browser storage patterns (see [data models](./data-models-excalidraw-app.md)).
- **No server-first SQL schema** lives in this repository; backend contracts are not defined as first-party REST routes here.

## Integrations (host app)

Identified from manifests and directory layout (quick scan):

- **Firebase** — client SDK dependency in `excalidraw-app`.
- **Socket.io client** — real-time collaboration transport.
- **Sentry** — error reporting (build flags can disable for certain targets).
- **i18next** — language detection in the app shell.

## Component overview (high level)

- **`packages/excalidraw`:** Editor surface, toolbars, scene graph, history, export, localization bundles.
- **`excalidraw-app/components`:** App chrome (menus, welcome, sidebars, promo banners, error boundary).

## Development workflow

See [development-guide.md](./development-guide.md).

## Deployment architecture

See [deployment-guide.md](./deployment-guide.md).

## Testing strategy

- Root scripts run **typecheck**, **ESLint**, **Prettier**, and **Vitest** across the workspace.
- App-level snapshots/tests under `excalidraw-app/tests`.

## Project-specific constraints (AI / contributors)

Repository rules under `.cursor/rules/` highlight:

- **State:** Prefer the editor action system (`actionManager.executeAction()` / `ExcalidrawAPI.executeAction(...)`) over store-style dispatch; core type `AppState` in `packages/excalidraw/types.ts`.
- **Rendering:** Canvas pipeline; avoid replacing with alternative canvas libraries without explicit intent.
- **Dependencies:** Avoid adding npm packages without approval; prefer `packages/utils` for helpers.

Protected hot spots are listed in `.cursor/rules/do-not-touch.mdc` (renderer, restore, action manager, core types).
