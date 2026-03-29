# Install, validate, and run

Prepare the monorepo, run the full local quality gate, then start the dev server. **Execute the shell steps yourself** from the **repository root** (do not only suggest commands).

## Prerequisites

- **Node.js** ≥ 18 (CI uses **20.x** — prefer 20 if something fails only on older Node).
- **Yarn** classic (see root `package.json` `packageManager`).

## Steps

### 1. Install dependencies

```bash
yarn install
```

If install fails, fix the reported issue (network, engine, lockfile) or summarize the error for the user.

### 2. Validate (same bar as local PR hygiene)

Run the full check suite:

```bash
yarn test:all
```

This runs typecheck, ESLint (max warnings 0), Prettier list-different, Vitest, and related scripts per root `package.json`.

- **If any step fails:** stop. Print the failing command output, suggest the minimal fix, and **do not** start the dev server until the user agrees or validation passes after a fix.

### 3. Run the project

Start the Vite dev server for `excalidraw-app`:

```bash
yarn start
```

- Run this as a **long-running / background** process (dev server stays up).
- When it is ready, tell the user the **local URL** from the Vite output (typically `http://localhost:5173` or similar — quote whatever the terminal prints).

## Optional (user asks for production-like run)

After a successful `yarn test:all`, they may want a production build instead of dev:

```bash
yarn build
yarn start:production
```

(Second command serves the built app — also long-running; use background.)

## Summary for the user

After success, report:

1. Install: OK  
2. `yarn test:all`: OK (or what failed)  
3. Dev server: running + URL  
