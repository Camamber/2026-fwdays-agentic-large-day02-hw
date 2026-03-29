# Data models — excalidraw-app / editor (quick scan)

## Summary

There are **no SQL migrations or Prisma schemas** in this repository. Persistence is **client-side** and **document-centric**.

## Scene / document model

- Drawings are represented as **JSON** (`.excalidraw` / internal scene format) managed by `packages/excalidraw` (types centered on `AppState` and element collections — see codebase; `packages/excalidraw/types.ts` is a protected hotspot per project rules).

## Browser storage

- **`idb-keyval`** is a dependency of `excalidraw-app`, indicating **IndexedDB key-value** usage for local persistence (exact keys and shapes require deep scan of `excalidraw-app/data/`).

## Server-side schema

- **Not in repo** for quick scan. Any server schema for collaboration or sharing lives outside this codebase or in external services.

## Next steps

- Deep scan: read `excalidraw-app/data/` and serialization paths under `packages/excalidraw/data/` for precise field-level documentation.
