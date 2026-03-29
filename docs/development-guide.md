# Development guide

## Prerequisites

- **Node.js** >= 18 (see root `package.json` / `engines`).
- **Yarn** 1.x (classic), matching `packageManager` in root `package.json`.

## Install

From the repository root:

```bash
yarn
```

## Common commands

| Goal                                | Command                 |
| ----------------------------------- | ----------------------- |
| Run the web app (dev)               | `yarn start`            |
| Production-like serve (after build) | `yarn start:production` |
| Build workspace packages (ESM)      | `yarn build:packages`   |
| Build full app                      | `yarn build`            |
| Run unit tests (Vitest)             | `yarn test`             |
| Full local verification             | `yarn test:all`         |
| Typecheck                           | `yarn test:typecheck`   |
| Lint                                | `yarn test:code`        |
| Format check                        | `yarn test:other`       |
| Autofix lint                        | `yarn fix:code`         |
| Autofix format                      | `yarn fix:other`        |

## Environment and configuration

- Vite drives `excalidraw-app`; environment variables may be prefixed with `VITE_` (see app scripts and Vite docs).
- Example: Sentry can be disabled in specific Docker builds via `VITE_APP_DISABLE_SENTRY` (see `excalidraw-app/package.json` scripts).

## Working on packages vs app

- **Library changes:** edit under `packages/*`, then rebuild packages (`yarn build:packages`) or rely on workspace linking as configured.
- **Host-only changes:** edit under `excalidraw-app/`.

## Examples

- `yarn start:example` — builds packages and starts the `examples/with-script-in-browser` demo (see root `package.json`).

## Further reading

- Upstream development documentation: [docs.excalidraw.com — Development](https://docs.excalidraw.com/docs/introduction/development).
