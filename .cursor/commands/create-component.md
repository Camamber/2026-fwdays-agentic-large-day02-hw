# Create component

Create a new **React function component** in this repo following project rules. Do not modify protected files listed in `.cursor/rules/do-not-touch.mdc`.

## Before writing code

1. **Confirm target** with the user if unclear:
   - **`excalidraw-app/`** — app shell UI (menus, collab chrome, etc.).
   - **`packages/excalidraw/`** — editor UI and core-adjacent components.
2. **Name**: PascalCase component name (e.g. `SharePanel`). File name **`SharePanel.tsx`** (PascalCase for components per `.cursor/rules/conventions.mdc`).
3. **Folder**: place next to related features or in the existing `components/` subtree for `excalidraw-app`; mirror sibling files in `packages/excalidraw` for editor components.

## Implementation checklist

- **Functional component + hooks only** — no class components.
- **Named export only** — `export const SharePanel = …` (no default export), except the user explicitly asks for an entry file pattern that already uses default in this repo (`App.tsx` is special).
- **Props type**: `type SharePanelProps = { … }` (prefer `type` for simple props per conventions).
- **Imports**: `import type { … }` for type-only imports; respect `import/order` and `.cursor/rules/imports-eslint.mdc`. In **`packages/excalidraw`**, do not import from the `@excalidraw/excalidraw` barrel — use relative paths to specific modules.
- **`excalidraw-app`**: do **not** import `"jotai"` directly — use `editor-jotai` / `app-jotai` (see `.eslintrc.json`).
- **Styles**: follow neighbors (SCSS module or `.scss` colocated if that’s the pattern in the folder).
- **Tests**: add colocated **`SharePanel.test.tsx`** (or `.test.ts`) with at least a smoke render or meaningful unit test; align with Vitest + Testing Library patterns in nearby tests.

## After implementation

1. Run **`yarn test:code`** and **`yarn test:other`** on touched files (or full **`yarn test:all`** if multiple packages changed).
2. Run **`yarn test`** (or scoped vitest) so the new test file passes.
3. If the component is under **`packages/*`** and consumed by the app, ensure **`yarn build:packages`** still succeeds when APIs or exports changed.

## Output

- Show the list of **created/changed files**.
- Summarize **props** and **where the component is used** (or note “not wired yet” if the user only asked for the file).
