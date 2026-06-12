# CLAUDE.md — Library / Package Template

> For published packages (npm/PyPI/crates). The defining constraint: OTHER PEOPLE'S CODE depends on yours — public API changes are breaking changes, and the bar for them is high.

```markdown
# {{LIBRARY_NAME}}

{{ONE_SENTENCE: what this library does}} Published to {{npm as `{{name}}` / PyPI / crates.io}}; semver applies.

## Commands

- Tests: `{{npm test}}` (watch: `{{npm test -- --watch}}`)
- Lint + typecheck: `{{npm run lint && npm run typecheck}}`
- Build (what ships): `{{npm run build}}` → `dist/`
- Docs: `{{npm run docs}}`
- Check what would be published: `{{npm pack --dry-run}}`

## The public API contract

- Public surface = what `{{src/index.ts}}` exports. EVERYTHING else is internal.
- Changing/removing a public export, narrowing an accepted type, widening a returned type, throwing in a place that didn't throw: ALL breaking → major version, and require explicit approval first.
- Additive (new export, new optional param): minor. Behavior-preserving fix: patch.
- When in doubt whether something is breaking: it is.

## Design rules

- Zero runtime dependencies unless unavoidable (each one is a tax on every user); dev/build deps are fine
- No side effects on import — importing the library must do nothing
- Errors: throw typed errors ({{`{{Name}}Error` subclasses}}) with actionable messages; never `throw "string"`
- Support targets: {{Node >= 20, evergreen browsers / Python >= 3.10}} — no APIs newer than the floor
- Everything public has JSDoc/docstrings with an example — docs are generated from them

## Testing

- Public API behavior, not internals — tests should survive a refactor
- Every bugfix adds a regression test that fails before the fix
- Type-level tests for the public types ({{tsd / expect-type}}) where applicable

## Definition of done

1. Lint + typecheck + tests green
2. No accidental public surface change (`{{npm run api-check / api-extractor}}`)
3. JSDoc/docstring + example on anything new and public
4. CHANGELOG entry under "Unreleased" describing the change in user terms

## Do NOT touch

- Version field (release tooling owns it), `dist/`, generated API reports
- Published behavior under a deprecation cycle — deprecate first ({{@deprecated + console warning}}), remove in the next major
```
