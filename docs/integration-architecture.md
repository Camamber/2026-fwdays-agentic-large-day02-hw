# Integration architecture (monorepo)

## Parts

1. **Workspace libraries** — `packages/common`, `packages/element`, `packages/math`, `packages/utils`, `packages/excalidraw`.
2. **Host application** — `excalidraw-app` consumes the published-style entry `@excalidraw/excalidraw` via Yarn workspaces.

## Dependency flow

```
examples/*  ──►  @excalidraw/*  (optional consumers)

excalidraw-app  ──►  @excalidraw/excalidraw (+ related workspace packages)
                         ▲
packages/excalidraw  ────┘
        ▲
packages/{common,element,math,utils}
```

## Build order

Root scripts build dependent packages before the app where needed (`yarn build:packages` then app build paths).

## External integration points (browser)

The host app integrates with **third-party services** (not defined as first-party HTTP route handlers in this repo):

| Direction | Mechanism | Notes |
| --- | --- | --- |
| Real-time collab | Socket.io client | See `excalidraw-app/collab/` |
| Backend services | Firebase client SDK | Dependency in `excalidraw-app` |
| Error reporting | Sentry browser SDK | Optional disable via build env |
| Analytics / tracking | Build-time flags (e.g. `VITE_APP_ENABLE_TRACKING`) | See app build scripts |

## Data flow (conceptual)

- **Editor state** lives in the core editor packages; the app shell wraps persistence, sharing, and network sync.
- **Exported documents** (`.excalidraw` JSON) cross the boundary between editor and storage/share features.
