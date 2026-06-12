# CLAUDE.md — API Service Template

> Copy to your repo root as `CLAUDE.md`, replace `{{PLACEHOLDERS}}`, delete what doesn't apply. Keep it short and imperative.

```markdown
# {{SERVICE_NAME}}

{{ONE_SENTENCE: what this service owns and who calls it}}

## Stack

- Runtime: {{e.g. Node 22 + Fastify / Python 3.12 + FastAPI / Go 1.23 + chi}}
- Database: {{e.g. Postgres 16 via {{ORM/driver}}; migrations in `migrations/`}}
- Cache/queues: {{e.g. Redis for cache, BullMQ for jobs}}
- API style: {{REST + OpenAPI in `openapi.yaml` / gRPC protos in `proto/`}}

## Commands

- Run locally: `{{make dev}}` (deps: `{{docker compose up -d db redis}}`)
- Tests: `{{make test}}`; integration tests need the compose stack up
- Lint + typecheck: `{{make lint}}` — must be clean before done
- New migration: `{{make migration name=...}}` — NEVER edit applied migrations

## Architecture map

- `src/routes/` (thin: parse → call service → shape response)
- `src/services/` (business logic — this is where behavior lives)
- `src/repos/` (data access only; no business rules)
- `src/lib/` (clients, config, shared utilities)
- Request flow: route → zod/schema validation → service → repo → DB

## API conventions

- Error envelope, always: `{ "error": { "code": "MACHINE_READABLE", "message": "human readable" } }`
- Pagination: cursor-based (`?cursor=&limit=`), never offset for public endpoints
- Versioning: {{URL prefix /v1/ — breaking changes require a new version}}
- All write endpoints idempotent or accepting an `Idempotency-Key`
- Validate at the boundary: nothing past the route layer handles raw input

## Conventions

- No business logic in routes or repos
- Every external call has a timeout and is wrapped in error mapping
- Logs are structured ({{pino/zap}}); never log secrets, tokens, or full request bodies
- Config via env only, read once in `src/lib/config` — no `process.env` elsewhere

## Definition of done

1. Lint + typecheck + tests green
2. New endpoints documented in {{openapi.yaml}} (run api-contract-check if unsure)
3. Migration has a tested rollback
4. Errors return the standard envelope, with a machine-readable code

## Do NOT touch

- Applied migrations, `{{*.generated.*}}`, `.env*`
- Public API shapes without explicit approval — clients depend on them
```
