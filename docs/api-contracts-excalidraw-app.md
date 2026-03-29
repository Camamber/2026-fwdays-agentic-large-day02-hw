# API contracts — excalidraw-app (quick scan)

## Summary

This repository does **not** ship a first-party HTTP route layer (no Express/Fastify/Nest app in-tree). “APIs” relevant to the product are:

1. **Third-party client SDKs** (Firebase, Socket.io client, Sentry).
2. **Implicit contracts** with whatever servers those clients connect to (hosted collaboration / Firebase project — configuration is environment-specific and not fully described in this quick scan).

## REST / OpenAPI

- **Not applicable** in-repo for quick scan. No `openapi.yaml` or route table was located via pattern search.

## Real-time

- **Socket.io client** (`socket.io-client` dependency) — actual events and payloads require reading `excalidraw-app/collab/` (deep scan recommended if you need a contract catalog).

## Firebase

- **Firebase** v11 client dependency — usage sites and API surface require code read (deep scan).

## Recommendations

- For **brownfield PRD** items touching collaboration or cloud sync, run a **deep** documentation pass targeting `excalidraw-app/collab/` and `excalidraw-app/data/`.
