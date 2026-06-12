---
name: tdd-loop
description: Enforce strict red-green-refactor TDD - write one failing test, verify it fails for the right reason, implement minimally, verify green, refactor under green. Use when implementing new behavior, fixing a bug with test coverage, or whenever the user asks for test-driven development.
---

Drive every line of implementation through the red-green-refactor cycle. The test is written first, watched fail, and only then satisfied with the minimum code possible. One behavior per loop iteration. This skill exists to prevent the two classic failures: writing implementation before tests, and writing tests that never failed (and therefore prove nothing).

## Steps

1. Decompose the request into a numbered list of discrete, testable behaviors (e.g. "returns 0 for empty cart", "applies 10% discount at 10+ purchases", "throws on negative quantity"). Each behavior is exactly one loop iteration. Track them with the todo list.
2. Detect the test runner before writing anything: check `package.json` scripts, `pytest.ini`/`pyproject.toml`, `go.mod`, `Cargo.toml`, existing test files for conventions (file naming, assertion library, mock style). Match the existing style exactly.
3. Verify the baseline: run the existing suite once. If it is already red, STOP and report — never start TDD on a broken baseline; you cannot attribute new failures.
4. RED — write exactly ONE new failing test for the next behavior in the list. Name it after the behavior, not the function ("applies_discount_at_ten_purchases", not "test_calculate_2"). Assert on observable outcomes, not internals.
5. Run only that test (e.g. `npx vitest run -t "name"`, `pytest path::test_name`, `go test -run Name`). Verify it fails for the RIGHT reason: an assertion failure showing expected vs actual. If it fails with ImportError/NameError/compile error instead, add only the minimal scaffolding (empty function, class stub returning nothing) and re-run until the failure is an assertion failure. Record the failure message.
6. If the new test passes immediately, treat it as a defect in the loop: either the behavior already exists (delete the test or keep it as a characterization test, skip to the next behavior) or the test asserts nothing meaningful — strengthen it until it genuinely fails.
7. GREEN — write the minimal implementation that makes the test pass. Resist generalizing: hard-coded returns and naive branches are acceptable if a later test in your behavior list will force the generalization. Do not handle cases no test demands.
8. Run the single test (must pass), then the FULL suite (must pass). A green test with a red suite means you broke something — fix before proceeding.
9. REFACTOR — only under a fully green suite: remove duplication, improve names, extract helpers. Re-run the full suite after each distinct refactor move. If it goes red, revert that move immediately rather than debugging forward.
10. Mark the behavior done and loop to step 4 for the next one. After the final behavior, run the entire suite once more plus coverage if available (`--coverage`, `pytest --cov`), and confirm every behavior from step 1 has a corresponding test.

## Output

- The behavior list with each behavior mapped to its test name and file path.
- For each loop: the recorded red failure message and the green confirmation.
- Final full-suite result (command + pass count) and coverage delta if measured.
- Any behaviors that turned out to already exist (with the characterization test kept).

## Rules

- NEVER write implementation code before a failing test exists for it.
- NEVER write more than one new failing test at a time.
- A test that was never seen failing does not count as a TDD test — re-induce the failure (stash the impl or invert the assertion temporarily) if in doubt.
- Wrong-reason failures (import/syntax/type errors) do not count as RED.
- Refactoring happens only when the full suite is green; revert rather than debug a red refactor.
- Do not weaken or delete an existing test to get to green without flagging it to the user first.
