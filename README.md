````md
# Svelte Template Setup Guide

## Prerequisites

1. Uninstall all existing Node.js versions
2. Install [NVM (Node Version Manager)](https://github.com/coreybutler/nvm-windows)
   - If your Windows username has a space, set a different installation path
3. Restart your terminal and verify NVM installation by running:

   ```bash
   nvm version
   ```
````

---

## Setup Instructions

### 1. Install Node.js

```bash
nvm install lts
nvm use lts
```

### 2. Create New Project

```bash
npx sv create "your-project-name"
cd your-project-name
```

### 3. Add Development Dependencies

```bash
npm install -D tailwindcss eslint prettier @sveltejs/adapter-auto playwright vitest
```

---

## Development

### Start Development Server

```bash
npm run dev
```

### Run Tests

```bash
# Unit tests
npm test

# End-to-end tests
npm run test:e2e
```

---

## Project Structure Recap

```text
svelte_template/
└─ template/
   ├─ .svelte-kit/             # generated build artifacts (ignore, not committed)
   ├─ e2e/                     # end-to-end tests (Playwright)
   ├─ src/                     # application source
   │  ├─ lib/                  # reusable code/assets ($lib alias)
   │  ├─ routes/               # file-based routes (+page.svelte, +layout.svelte)
   │  ├─ app.css               # global styles (Tailwind v4 entry)
   │  ├─ app.d.ts              # ambient type definitions (extend App.* here)
   │  ├─ app.html              # HTML shell (injected with built app)
   ├─ static/                  # static assets served as-is (/robots.txt, icons)
   ├─ .gitignore               # files/folders Git should ignore
   ├─ .npmrc                   # npm configuration
   ├─ .prettierrc              # Prettier formatting rules
   ├─ eslint.config.js         # ESLint linting rules
   ├─ package.json             # dependencies & npm scripts
   ├─ package-lock.json        # exact dependency tree (auto-generated)
   ├─ playwright.config.ts     # Playwright E2E test config
   ├─ svelte.config.js         # SvelteKit config (adapter, preprocessors)
   ├─ tsconfig.json            # TypeScript config (extends .svelte-kit defaults)
   ├─ vite.config.ts           # Vite bundler/dev-server config
   └─ vitest-setup-client.ts   # setup file for Vitest tests
```
