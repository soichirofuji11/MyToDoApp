# Repository Guidelines

## Project Structure & Module Organization
- `src/app/` — App Router pages, layouts, and global styles (`globals.css`). Add routes as folders: `src/app/<routes>/page.tsx`.
- `public/` — Static assets served from root (e.g., `/icon.png`).
- `next.config.ts` — Next.js configuration. Keep changes minimal and documented in PRs.
- No server code yet; API routes can live under `src/app/api/<route>/route.ts`.

## Build, Test, and Development Commands
- `npm run dev` — Start local dev server with Turbopack.
- `npm run build` — Production build.
- `npm start` — Run the production server.
- `npm run lint` — Lint with ESLint (Next + TypeScript rules).

## Coding Style & Naming Conventions
- TypeScript throughout; prefer explicit types on public APIs and components.
- Indentation: 2 spaces; keep lines focused and readable.
- React components: PascalCase (`TaskList.tsx`); hooks: `useXxx.ts`.
- Files colocate with features when reasonable (e.g., `src/app/todos/components/`).
- App Router: route segments are folders; `page.tsx` renders a route, `layout.tsx` defines shared UI.
- Styling: Tailwind CSS utility-first in JSX; global resets in `globals.css`. Keep class names ordered logically (layout → spacing → color).
- Run `npm run lint` before pushing; ESLint is configured via `eslint.config.mjs` (Next core-web-vitals, TS).

## Testing Guidelines
- Tests are not set up yet. Recommended: Vitest + React Testing Library for unit/component tests and Playwright for E2E.
- Suggested patterns: unit `**/*.test.ts(x)`, E2E under `e2e/`.
- Aim for critical-path coverage (state, routing, and form handlers). Add `npm test` script when tests land.

## Commit & Pull Request Guidelines
- Use Conventional Commits: `feat:`, `fix:`, `chore:`, `docs:`, `refactor:`, etc.
- Keep commits scoped and atomic; include rationale in the body when non-trivial.
- PRs must include: clear description, screenshots/GIFs for UI changes, steps to test, and linked issues (e.g., `Closes #123`).

## Branching Model (GitHub Flow)
- Branch from `main` using short-lived branches: `feature/<summary>`, `fix/<summary>`, `chore/<summary>`.
- Open a PR early for visibility; keep it focused and small.
- Require review + green lint/build before merge; avoid direct commits to `main`.
- Prefer “Squash and merge”, then delete the branch.

## Security & Configuration Tips
- Store secrets in `.env.local`; never commit `.env*`. Reference via `process.env` and mark client-safe variables with `NEXT_PUBLIC_`.
- Avoid leaking server-only values into client components.
- Verify Node.js LTS (>=18) and matching package manager versions before building.
