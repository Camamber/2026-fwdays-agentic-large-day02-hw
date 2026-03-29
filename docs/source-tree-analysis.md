# Source tree analysis (quick scan)

Annotated high-level layout of the repository. Paths are relative to the repository root.

```
.
├── excalidraw-app/          # Host web app (Vite + React): entry for `yarn start`
│   ├── App.tsx              # Application root
│   ├── components/          # App-level UI (menus, footer, welcome, collab UI pieces)
│   ├── collab/              # Real-time collaboration wiring
│   ├── data/                # App data / persistence helpers
│   ├── share/               # Sharing / export flows
│   ├── app-language/        # Language / locale helpers for the shell
│   ├── tests/               # App-level tests
│   └── vite.config.mts      # Vite configuration
├── packages/
│   ├── excalidraw/          # Main editor package (@excalidraw/excalidraw): canvas, actions, components
│   ├── common/              # Shared types/utilities across packages
│   ├── element/             # Scene elements / geometry helpers
│   ├── math/                # Math utilities
│   └── utils/               # Low-level helpers
├── examples/                # Sample integrations (e.g. with-nextjs, with-script-in-browser)
├── scripts/                 # Root build / tooling scripts
├── dev-docs/                # Docusaurus-oriented notes (see README inside)
├── .github/workflows/       # CI: test, lint, docker, release, locales, etc.
├── package.json             # Workspace root: scripts orchestrate app + packages
└── README.md                # Upstream product readme
```

## Critical directories

| Path | Role |
| --- | --- |
| `packages/excalidraw` | Core editor: scene, rendering, actions, i18n assets |
| `excalidraw-app` | Runnable product shell; integrates Firebase, Socket.io client, Sentry |
| `packages/common`, `element`, `math`, `utils` | Shared libraries consumed by `excalidraw` and tooling |
| `examples/*` | Integration patterns for consumers |

## Entry points (development)

- **Local dev server:** `yarn start` → runs Vite in `excalidraw-app`.
- **Package builds:** `yarn build:packages` builds workspace libraries (ESM) used by the app.

## Notes

- `node_modules`, `dist`, and build outputs are excluded from this tree; they appear after install/build.
- Quick scan does not enumerate every subdirectory under `packages/excalidraw` (large); use IDE search or a deep scan for exhaustive inventory.
