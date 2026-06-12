---
name: api-contract-check
description: Detect drift between an API's contract (OpenAPI/docs/types) and its actual implementation - enumerate both sides, diff in both directions, compare schemas field by field, and report a severity-ranked drift table. Use when verifying docs accuracy, before publishing an API, or when clients report mismatches.
---

Find every place the documented API and the implemented API disagree. Drift is checked in both directions — routes that exist but are undocumented, and documented routes that do not exist — and then at field level for the endpoints that match, because the subtle killers are renamed fields, changed types, and undeclared status codes.

## Steps

1. Locate the contract sources: `Glob` for `**/*openapi*.{json,yaml,yml}`, `**/swagger*.{json,yaml,yml}`, `**/*.proto`, GraphQL schemas, API docs under `docs/`, and exported client types (TS interfaces, generated SDKs). If multiple contracts exist, ask which is authoritative or check all and label findings per source.
2. Parse the DECLARED surface into a normalized list: `METHOD /path` plus, per endpoint, request params/body schema (field name, type, required?), response schema per status code, and declared status codes. Normalize path parameter syntax (`{id}` vs `:id` vs `<id>`) before comparison.
3. Enumerate the ACTUAL surface from code: grep route registrations for the framework in use — Express/Koa `(app|router)\.(get|post|put|patch|delete|all)\(`, FastAPI/Flask `@(app|router|bp)\.(get|post|put|patch|delete|route)`, Spring `@(Get|Post|Put|Patch|Delete|Request)Mapping`, Rails `config/routes.rb` (or run `rails routes` if the environment allows), Go `mux.HandleFunc`/`r.Get(`. CRITICAL: resolve mount prefixes — follow `app.use("/api/v1", router)`, blueprint prefixes, and class-level mappings so each route is recorded as its FULL path. Note middleware-generated routes (auto-CRUD, static mounts) explicitly.
4. Diff direction A — implemented but undocumented: every actual `METHOD /path` absent from the contract. These are invisible API surface (often security-relevant).
5. Diff direction B — documented but unimplemented: every declared endpoint with no matching handler, plus near-misses worth calling out separately: method mismatch (doc says PUT, code has PATCH) and path-shape mismatch (`/users/{id}` vs `/user/:id`).
6. Field-level comparison for matched endpoints: read each handler and compare against the schema —
   - Request: fields the handler reads/validates vs declared fields; required-in-doc but unvalidated in code; accepted-in-code but undeclared.
   - Response: fields actually serialized vs declared (missing declared field, extra undeclared field, type mismatch, nullability drift, enum values out of sync).
   - Status codes: codes the handler can return (including error paths and validation failures) vs codes declared.
7. Assign severity per drift: HIGH = breaks existing clients (declared response field missing/retyped, documented endpoint absent, method mismatch); MEDIUM = undocumented but live surface (extra endpoints/fields clients may already depend on); LOW = stale doc detail with no client impact (descriptions, examples).
8. Compile the report table and a remediation pointer per row: "fix code" when the contract is the source of truth, "fix contract" when behavior is intentional, "decide" when unclear — never silently pick a side on HIGH items.

## Output

- Drift table: `endpoint | declared | implemented | drift type | severity | suggested side to fix`.
- Field-level mismatch list for matched endpoints, with file:line for the handler and the contract location.
- Summary counts: endpoints checked, matches, direction-A drift, direction-B drift, field-level issues by severity.
- Explicit statement of which contract file was treated as authoritative.

## Rules

- Always diff BOTH directions; a one-way check misses half the drift.
- Resolve route prefixes/mounts before comparing — comparing relative paths produces garbage findings.
- Field findings require reading the handler (and its serializer/validator), not just the route line.
- Report drift; do not modify code or contract unless the user chooses a side and asks.
- If routes are generated dynamically beyond static analysis (reflection, decorators with computed paths), list those endpoints as UNVERIFIABLE rather than guessing.
