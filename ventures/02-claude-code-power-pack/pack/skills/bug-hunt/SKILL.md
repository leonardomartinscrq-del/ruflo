---
name: bug-hunt
description: Systematic bug investigation - pin down expected vs actual, build a minimal reproduction, bisect code paths/inputs/versions, state the root cause mechanism, then ship a minimal fix with a regression test. Use when debugging a reported defect, a flaky failure, or any "it doesn't work" report.
---

Hunt bugs by reproduction and bisection, not by staring and guessing. No fix is written until the bug is reproduced on demand and the root cause is stated as a mechanism. The minimal repro you build becomes the regression test, so the bug can never silently return.

## Steps

1. Extract the contract violation. Write two one-line statements: EXPECTED (what should happen, per docs/tests/user intent) and ACTUAL (what happens, with the exact error text or wrong value). If either is vague, interrogate the evidence first — logs, stack traces, failing CI output — until both are concrete and falsifiable.
2. Reproduce before anything else. Write the smallest runnable artifact that demonstrates the bug — a failing test, or a script in `/tmp/repro.*`. Run it and confirm it fails with the reported symptom. If you cannot reproduce, STOP and report precisely what additional information is needed (versions, data, environment); never fix blind against an unreproduced bug.
3. Shrink the repro aggressively: remove inputs, config, dependencies, and steps one at a time; keep a removal only if the bug still reproduces. You are done shrinking when removing anything else makes the bug disappear. Each thing whose removal kills the bug is a clue.
4. Bisect the surface — binary-search along whichever axis fits:
   - Code path: instrument the midpoint of the suspected flow (assert/log the state there); determine if corruption happens before or after; recurse into the bad half.
   - Input: halve the failing input/dataset; recurse into the half that still fails (delta debugging).
   - History: if a known-good version exists, `git bisect start; git bisect bad HEAD; git bisect good <sha>` and use the repro script as the oracle (`git bisect run <script>` when it exits nonzero on failure).
5. State the root cause as a mechanism: "X happens because Y does Z when condition W." It must explain WHY, not just point at a line. Test it: if the statement contains "somehow" or "for some reason", you are not done — keep bisecting. Verify the mechanism predicts the symptom (e.g. it explains why only certain inputs fail).
6. Write the minimal fix: the smallest change that breaks the causal mechanism at the right layer (fix the cause, not the symptom — no upstream `try/catch` band-aids over a downstream logic error). No drive-by refactors, renames, or formatting in the same change.
7. Convert the shrunk repro into a permanent regression test in the test suite, named after the bug (reference the issue ID if one exists). Prove it works both ways: with the fix stashed/reverted it must fail; with the fix applied it must pass. Then run the FULL suite to confirm no collateral damage.
8. Sweep for siblings: grep for the same pattern elsewhere in the codebase (same misuse of the API, same unchecked condition). Report look-alikes as follow-ups rather than silently expanding the fix.

## Output

- EXPECTED vs ACTUAL statements.
- The minimal reproduction (test path or script) and the bisection trail (what was ruled out, in what order).
- Root-cause statement in the "X because Y does Z when W" form, citing file:line.
- The fix diff summary and the regression test path, with red-without-fix / green-with-fix evidence.
- Full-suite result and any sibling occurrences flagged for follow-up.

## Rules

- No fix before a reproduction exists and fails on demand.
- No fix before the root cause is stated as a mechanism; "this change makes the symptom go away" is not a root cause.
- The regression test must be proven to fail without the fix — a test that never went red proves nothing.
- Fix and refactor are separate changes; keep the fix diff minimal.
- If reproduction is impossible with the available information, deliver the precise list of what is missing instead of a speculative patch.
