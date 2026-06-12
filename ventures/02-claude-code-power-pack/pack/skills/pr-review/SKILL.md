---
name: pr-review
description: Full local review of a branch diff against its base - gather the diff and intent, review in four ordered passes (correctness, security, tests, design), emit severity-tagged findings and an approve/request-changes verdict. Use when asked to review a PR, branch, or pending changes before merge.
---

Perform a disciplined, multi-pass review of the current branch's diff against its base. The diff alone is not enough: you review the change against its stated intent, and you read enough surrounding code to judge whether callers and invariants still hold. Findings are severity-tagged so the author can triage; the verdict is earned, not vibes.

## Steps

1. Establish the base and scope. Find the default branch (`git remote show origin | grep "HEAD branch"`, fall back to `main`/`master`), then compute the fork point: `BASE=$(git merge-base HEAD origin/<default>)`. Gather scope: `git diff --stat $BASE...HEAD` and `git log --oneline $BASE..HEAD`. If `gh pr view --json title,body` works, capture the PR description too.
2. Write the intent statement: one sentence of what this change claims to do, derived from commits/description. Every pass below reviews against this claim. If the diff contains substantial changes unrelated to the claim, flag scope creep as a finding.
3. Read the full diff with context: `git diff $BASE...HEAD`. For any changed function whose callers are off-screen, grep the call sites — a correct-looking diff can still break callers.
4. PASS 1 — Correctness. Hunt specifically for: off-by-one and boundary conditions (empty, single, max); null/undefined/None on new paths; error paths that swallow or mis-wrap exceptions; missing `await`/unhandled promises; mutation of shared or passed-in state; concurrency on shared resources; behavior changes to existing call sites; resource leaks (unclosed handles, missing cleanup in early returns).
5. PASS 2 — Security. New external inputs validated at the boundary? String-built SQL/shell/path/template from user data? AuthN/authZ present on new or changed routes? Secrets or credentials introduced in code or config? Lockfile diff adds packages — are they expected and reputable? Sensitive data in new log lines?
6. PASS 3 — Tests. Map each new behavior from the intent statement to a test. Read the tests: do they assert outcomes, or merely "doesn't throw"? Are failure paths tested, not just happy paths? If the suite is cheap to run, run it and record the result. Missing tests for a behavior change is at least [major].
7. PASS 4 — Design. Public API shape and naming; duplication that should reuse existing helpers; files placed per repo conventions; dead code or commented-out blocks; backwards compatibility / semver implications; needless complexity relative to the problem.
8. Write findings as you go, one per line: `[severity] file:line — issue — suggested fix`. Severities: [blocker] must fix before merge (correctness/security defects, broken tests); [major] should fix before merge (missing tests, API problems); [minor] fix soon (cleanup, edge polish); [nit] optional style.
9. Verdict: REQUEST-CHANGES if any [blocker] or two or more [major]; otherwise APPROVE, listing the [minor]/[nit] items as non-blocking comments. State the verdict explicitly with its justification.

## Output

- Intent statement and scope summary (files, +/- lines, commit count).
- Findings list grouped by severity with file:line references.
- Test-coverage assessment mapping behaviors to tests (or gaps).
- Explicit verdict: APPROVE or REQUEST-CHANGES, with the rule that triggered it.

## Rules

- Always diff against the merge-base (`...`), never raw branch-to-branch, or you will review unrelated upstream commits.
- Never approve a diff you have not fully read; if the diff exceeds what you can read, say so and review the riskiest files first.
- Every [blocker] and [major] must cite a concrete file:line and a mechanism, not a feeling.
- Check call sites of changed signatures before claiming correctness.
- Do not modify any code during review; suggest, never apply, unless the user explicitly asks for fixes afterward.
