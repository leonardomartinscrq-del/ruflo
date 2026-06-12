---
name: codebase-tour
description: Generate a verified onboarding document for a repository - entry points, build/run/test commands proven by actually running them, a directory map with purposes, a core data-flow narrative, the first three files to read, and gotchas. Use when onboarding to an unfamiliar codebase or asked to document "how this repo works".
---

Produce an onboarding doc a new developer can trust, which means every command in it was executed during the tour and every directory purpose was inferred from reading representative files — not guessed from folder names. The doc optimizes for the first day: get it running, know where things live, know what to read first.

## Steps

1. Inventory the surface: list the repo root, read the README (note claims to verify later), read the manifests (`package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `Makefile`, `docker-compose.yml`, CI workflow files). Identify language(s), framework(s), and package manager from lockfiles, not assumptions.
2. Verify the lifecycle commands BY RUNNING THEM, in order: install -> build -> test -> run/dev. Source candidates from manifest scripts, Makefile targets, and CI steps (CI is often the most truthful). For each, record the exact command, whether it succeeded, how long it took, and any prerequisite discovered the hard way (env var, service, codegen step). If a command cannot be run in this environment, mark it `UNVERIFIED` in the doc — never present an untested command as working.
3. Locate entry points: `main`/`bin`/`exports` fields in the manifest, `if __name__ == "__main__"`, `func main()`, server bootstrap files, CLI command registration. List each with one line on what it starts.
4. Build the directory map: for each top-level directory (and key subdirectories), open 1-2 representative files and write a one-line purpose from what the code actually does. Flag dead-looking directories (no recent commits, no imports into them) as such instead of describing them confidently.
5. Trace one core data flow end to end: pick the most representative operation (an HTTP request, a CLI invocation, a job run) and follow it through real symbols — entry point -> routing/dispatch -> business logic -> persistence/external calls -> response. Write it as a short narrative naming concrete files and functions at each hop, so a reader can follow along in their editor.
6. Choose the "first 3 places to read": the files that most accelerate understanding. Good heuristics: the domain core (most-imported module — check import frequency with grep), the main entry point, and the central type/schema definitions. Justify each pick in one sentence.
7. Collect gotchas encountered during steps 2-5: required env vars and where to get values, codegen/migration steps that must precede builds, slow or order-dependent test suites, pinned tool versions, platform quirks, pre-commit hooks. Only include gotchas you observed or found documented — no invented warnings.
8. Write the document to `docs/ONBOARDING.md` (or the path the user specifies) with sections: Quick Start (verified commands), Entry Points, Directory Map, Core Data Flow, First 3 Places to Read, Gotchas. Lead the Quick Start with the shortest proven path from clone to running.

## Output

- `docs/ONBOARDING.md` containing all six sections.
- Every command annotated as verified (with this environment's result) or `UNVERIFIED` with the reason.
- The data-flow narrative citing concrete file paths and function names.
- A short summary to the user of anything broken discovered along the way (failing build/test out of the box is itself a key finding).

## Rules

- Never document a command you did not execute, unless it is explicitly marked `UNVERIFIED`.
- Directory purposes come from reading files inside them, not from the directory name.
- The data-flow trace must reference real, current symbols — re-check any path you cite.
- If the README contradicts observed reality, the doc records reality and notes the discrepancy.
- Keep it skimmable: one-liners over paragraphs everywhere except the data-flow narrative.
