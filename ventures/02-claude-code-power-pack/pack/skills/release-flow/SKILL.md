---
name: release-flow
description: Run a verified release - semver bump from commit history, changelog generation, version-reference updates, build-passes gate, annotated tag, and release-notes draft, with verification at every step. Use when cutting a release or when asked to bump and tag a version.
---

Execute a release as a gated checklist where every step is verified before the next begins. The cardinal rule: nothing gets tagged that did not build and pass tests in its final form. Version references are hunted across the whole repo, not just the manifest, because stale versions in docs and constants are the most common release defect.

## Steps

1. Preflight gate. Verify: working tree clean (`git status --porcelain` outputs nothing), on the release branch, up to date with remote (`git fetch && git status`). If dirty or behind, stop and resolve — never release uncommitted or stale state.
2. Determine the bump. Find the last release: `LAST=$(git describe --tags --abbrev=0)`. Review `git log $LAST..HEAD --oneline`. Apply semver discipline: any breaking change (API removal/rename, behavior change, schema change) -> MAJOR; new backward-compatible capability -> MINOR; fixes only -> PATCH. State the chosen version and the commit(s) that justify it; if ambiguous, ask rather than guess.
3. Bump the manifest: `package.json` / `pyproject.toml` / `Cargo.toml` (use the ecosystem command, e.g. `npm version X.Y.Z --no-git-tag-version`, so lockfiles stay consistent).
4. Hunt stale version references: `grep -rn "<old-version>" --include="*.{md,ts,js,py,toml,json,yaml,yml}" .` (exclude lockfiles and node_modules). Update every legitimate hit — README install lines, docs, `__version__`/`VERSION` constants, badge URLs, example snippets. Re-grep to confirm zero remaining legitimate hits.
5. Generate the changelog from commits, not memory: group `git log $LAST..HEAD` entries under Added / Changed / Fixed / Security / Breaking. Rewrite each as a user-facing sentence (what it means for users, not the commit message verbatim). Prepend a `## [X.Y.Z] - YYYY-MM-DD` section to `CHANGELOG.md`. Breaking changes get explicit migration instructions.
6. BUILD-PASSES GATE (never skip): run the full build, the full test suite, and the linter on the bumped tree. All three must pass on the exact code being released. Any failure aborts the release — fix, then restart from step 4's verification. Do not "tag now, fix after".
7. Commit and tag: `git commit -am "chore(release): vX.Y.Z"`, then an annotated tag `git tag -a vX.Y.Z -m "vX.Y.Z"`. Verify with `git tag -l vX.Y.Z` and `git show vX.Y.Z --stat` that the tag points at the release commit.
8. Draft release notes (separate from the changelog): 2-4 highlight bullets in plain language, a Breaking Changes section with migration steps, notable fixes, and a link/reference to the full changelog. Save the draft where the user can use it (e.g. `/tmp/release-notes-vX.Y.Z.md`) — do not publish or push unless explicitly asked.
9. Final verification echo: new version consistent everywhere (grep returns only changelog history for the old version), tag exists on the release commit, build artifacts present, notes drafted. Present this checklist with each item checked.

## Output

- The chosen version with semver justification.
- List of every file whose version reference was updated.
- Changelog section added (shown inline).
- Build/test/lint gate results (commands + pass confirmation).
- Tag name and the commit it points to.
- Release-notes draft and its location.

## Rules

- NEVER skip the build-passes gate; a release that did not build in final form is invalid.
- Never tag a dirty working tree or an unmerged/behind branch.
- Changelog comes from actual commit history, never from recollection.
- No `git push`, `npm publish`, or `gh release create` unless the user explicitly asks — tagging locally is the boundary of this skill.
- Pre-release suffixes (`-alpha.N`, `-rc.N`) only when explicitly requested.
- If any step fails, report the failure and stop; do not improvise past a failed gate.
