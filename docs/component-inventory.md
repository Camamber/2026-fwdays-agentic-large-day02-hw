# Component inventory (quick scan)

Quick scan uses **directory and filename patterns** only; this is not an exhaustive list of every React component.

## `excalidraw-app/components`

App-shell UI (sample of top-level files):

| File / area                          | Likely role                    |
| ------------------------------------ | ------------------------------ |
| `AppMainMenu.tsx`                    | Primary application menu       |
| `AppSidebar.tsx` / `AppSidebar.scss` | Sidebar layout and styles      |
| `AppFooter.tsx`                      | Footer chrome                  |
| `AppWelcomeScreen.tsx`               | First-run / welcome experience |
| `TopErrorBoundary.tsx`               | Error boundary for the shell   |
| `DebugCanvas.tsx`                    | Debugging aid                  |
| `AI.tsx`                             | AI-related UI entry            |
| `EncryptedIcon.tsx`                  | Encryption indicator           |
| `ExcalidrawPlusPromoBanner.tsx`      | Promotional banner             |
| `ExportToExcalidrawPlus.tsx`         | Export flow to Excalidraw+     |

## `packages/excalidraw`

Large package: contains `components/` subtree with editor UI, plus `actions/`, `data/`, `scene/`, `hooks/`, etc. For a full inventory, run a **deep** documentation scan or browse `packages/excalidraw/components` in the IDE.

## Design system

No separate design-system package was identified in the quick scan; styling mixes SCSS and component-level styles within packages.
