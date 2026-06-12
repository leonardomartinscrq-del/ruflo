# CLAUDE.md — Monorepo Template

> Copy to the monorepo root as `CLAUDE.md`. In a monorepo, the root file should stay an INDEX — put package-specific detail in `packages/*/CLAUDE.md`, which Claude Code picks up when working in that directory.

```markdown
# {{MONOREPO_NAME}}

{{ONE_SENTENCE: what this monorepo contains}}

## Layout

| Path | What it is | Owner-ish |
|---|---|---|
| `apps/{{web}}` | {{customer-facing app}} | {{team/area}} |
| `apps/{{api}}` | {{backend service}} | {{team/area}} |
| `packages/{{ui}}` | shared component library | shared |
| `packages/{{config}}` | shared tsconfig/eslint | shared |
| `packages/{{core}}` | domain types + logic shared by apps | shared |

Each app/package may have its own `CLAUDE.md` with specifics — read it before working there.

## Tooling

- Package manager: `{{pnpm}}` — ALWAYS `{{pnpm}}`, never npm/yarn (lockfile divergence breaks CI)
- Task runner: `{{turbo / nx}}`; tasks run from the ROOT:
  - All tests: `{{pnpm turbo test}}`
  - One package: `{{pnpm turbo test --filter={{pkg}}}}`
  - Lint + typecheck everything: `{{pnpm turbo lint typecheck}}`
- Adding a dependency: `{{pnpm add <dep> --filter <pkg>}}` — root-level installs need approval

## Cross-package rules

- Dependency direction: `apps/*` may depend on `packages/*`; packages NEVER depend on apps; `packages/core` depends on nothing internal
- Shared code changes (`packages/*`) can break multiple apps: after editing a package, run the affected graph: `{{pnpm turbo test --filter=...[HEAD]}}`
- Breaking a shared package's public API requires updating ALL consumers in the same change — no "I'll fix the other app later"
- New shared code goes in an existing package unless there's a strong reason; new packages need approval

## Conventions

- TypeScript strict everywhere; one tsconfig base in `packages/{{config}}`
- Internal imports via workspace aliases (`@{{scope}}/core`), never relative paths across package boundaries
- Generated artifacts (`dist/`, `*.generated.*`) are never hand-edited

## Definition of done

1. `{{pnpm turbo lint typecheck test}}` green from the root (not just in the package you touched)
2. Affected-graph tests pass for shared-package changes
3. No new circular dependencies ({{`pnpm turbo run check:cycles` / madge}})

## Do NOT touch

- `{{pnpm-lock.yaml}}` by hand; CI/release config in `{{.github/workflows}}` without approval
- Version fields in package.json — releases are handled by {{changesets/release tooling}}
```
