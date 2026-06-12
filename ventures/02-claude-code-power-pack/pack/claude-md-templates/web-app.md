# CLAUDE.md — Web App Template

> Copy to your repo root as `CLAUDE.md`, replace `{{PLACEHOLDERS}}`, delete sections that don't apply, and keep it under ~100 lines — CLAUDE.md is loaded into every session, so every line costs attention.

```markdown
# {{PROJECT_NAME}}

{{ONE_SENTENCE: what this app does and for whom}}

## Stack

- Framework: {{e.g. Next.js 15 (App Router) / Remix / SvelteKit}}
- Language: TypeScript (strict)
- Styling: {{e.g. Tailwind + shadcn/ui}}
- Data: {{e.g. Postgres via Prisma; TanStack Query on the client}}
- Auth: {{e.g. Auth.js, session cookies — NOT localStorage tokens}}

## Commands

- Dev server: `{{npm run dev}}`
- Tests: `{{npm test}}` (single file: `{{npm test -- path/to/file}}`)
- Lint + typecheck: `{{npm run lint && npm run typecheck}}` — run before declaring any task done
- Build: `{{npm run build}}`

## Architecture map

- `app/` — routes; server components by default, `"use client"` only when interactive
- `components/` — shared UI; `components/ui/` is generated (shadcn), don't hand-edit
- `lib/` — domain logic, API clients, utilities; framework-free where possible
- `{{db/ or prisma/}}` — schema and migrations
- Data flow: route loads data in server component → passes to client components as props → mutations via {{server actions / API routes}}

## Conventions

- Server-first: fetch on the server; client state only for UI state
- Forms: {{e.g. react-hook-form + zod schema in lib/validations/}} — validate on BOTH client and server
- Errors: user-visible failures use {{error.tsx boundaries / toast pattern}}; never swallow errors silently
- Naming: components PascalCase, files kebab-case, hooks `use*`
- No new dependencies without asking — bundle size is watched

## Definition of done

1. Lint + typecheck clean
2. Tests pass, new behavior has a test
3. Works with JS disabled where SSR applies (progressive enhancement)
4. No console.log left behind; no `any` introduced

## Do NOT touch

- `{{components/ui/}}` (generated), `{{*.generated.ts}}`
- Database migrations that are already applied — create a new one instead
- `.env*` files — tell the user what variable to add
```
