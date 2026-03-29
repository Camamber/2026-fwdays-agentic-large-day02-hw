# Deployment guide (quick scan)

## CI/CD

GitHub Actions workflows under `.github/workflows/` include (non-exhaustive):

| Workflow | Purpose (inferred from name) |
| --- | --- |
| `test.yml` | Automated tests |
| `lint.yml` | Linting |
| `test-coverage-pr.yml` | Coverage on PRs |
| `size-limit.yml` | Bundle size limits |
| `build-docker.yml` / `publish-docker.yml` | Docker image build and publish |
| `autorelease-excalidraw.yml` | Release automation for the package |
| `locales-coverage.yml` | Translation coverage |
| `sentry-production.yml` | Sentry-related production steps |
| `semantic-pr-title.yml` | PR title conventions |
| `cancel.yml` | Workflow cancellation hygiene |

## Docker

`excalidraw-app` defines `build:app:docker` using Vite with Sentry disabled for that target. See `excalidraw-app/package.json` scripts and Docker workflows for the canonical pipeline.

## Static hosting

The built app is a static SPA suitable for CDNs or static hosts (Vite output). Exact hosting (e.g. Vercel) is environment-specific; build scripts reference `VERCEL_GIT_COMMIT_SHA` for optional metadata.

## Operational notes

- Error reporting: Sentry in browser builds unless disabled by env flags.
- Quick scan does not document secrets management; follow your org’s standard for `VITE_*` and API keys.
