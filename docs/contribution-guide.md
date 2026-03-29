# Contribution guide (repository snapshot)

## Local policy

Root [CONTRIBUTING.md](../CONTRIBUTING.md) points to the official contribution documentation.

## Primary reference

- **Contributing:** [docs.excalidraw.com — Contributing](https://docs.excalidraw.com/docs/introduction/contributing)
- **Translating:** linked from the same contributing page on the official site.

## Pull requests

GitHub templates and automation live under `.github/` (for example `PULL_REQUEST_TEMPLATE.md`, semantic PR title workflow).

## Code quality

Before opening a PR, run from the repository root:

```bash
yarn test:all
```

(or the subset your change requires: typecheck, lint, tests, prettier).

## AI / Cursor conventions

See `.cursor/rules/` for architecture expectations and protected files (`do-not-touch.mdc`).
