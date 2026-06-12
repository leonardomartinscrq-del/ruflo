---
name: refactor-plan
description: Decompose a large refactor into PR-sized, individually shippable, reversible steps - map the blast radius, pin invariants with tests, order steps so each lands green, and schedule the point of no return last. Use when planning a migration, architecture change, or any refactor too big for one PR.
---

Turn a risky big-bang refactor into an ordered sequence of small steps where the codebase is shippable after every single one. The plan's quality is measured by two properties: any step can be reverted with one revert commit, and the irreversible moment is identified explicitly and pushed to the very end.

## Steps

1. Define the end state in one paragraph: what the code looks like after, and — just as important — what is explicitly OUT of scope. Refactors die from scope creep; write the non-goals down.
2. Map the blast radius: grep every import/call site of the code being moved or changed and count affected files per module. Separately list external consumers that cannot be atomically updated: public APIs, other repos/services, serialized data formats, database schemas, on-disk caches, published types. External consumers dictate where compatibility shims are mandatory.
3. Pin the invariants: list the behaviors that must hold throughout the entire refactor (outputs, API responses, data integrity, performance floors) and map each to the tests that enforce it. Where a to-be-changed path lacks coverage, the plan's Step 0 is writing characterization tests that capture CURRENT behavior — you cannot safely refactor what you cannot detect breaking.
4. Decompose into steps where each one: (a) leaves the full suite green and the system shippable, (b) is reviewable — target roughly under 400 changed lines, (c) is reversible via a single `git revert`, (d) has a one-line purpose. If a step fails any criterion, split it.
5. Prefer the expand/contract (strangler) shape: ADD the new implementation alongside the old -> route callers over incrementally (module by module, or behind a flag) -> CONTRACT by deleting the old path only after zero callers remain (verify with grep, not memory). Never modify-in-place when add-alongside is feasible.
6. Order the steps by risk: pure additions and test scaffolding first; behavior-preserving moves/renames next; caller migrations in dependency order (leaf modules before core); contract changes and deletions last.
7. Identify the POINT OF NO RETURN — the first step that cannot be cheaply reverted (destructive schema migration, data backfill, public API removal, published package break). Schedule it as late as possible, ideally dead last, and write its rollback/mitigation plan BEFORE it executes (backup, dual-write window, deprecation period). Everything before it must be safe to abandon.
8. For each step, write the four-field card: GOAL (one line) / FILES (paths or globs) / VERIFY (exact command that must pass) / ROLLBACK (revert commit, flag off, or restore action).
9. Stress-test the plan: simulate abandoning the refactor after each step and confirm the codebase is still consistent and shippable at every boundary. Any step whose abandonment leaves a broken half-state must be merged with its completing step or re-split.

## Output

- End-state paragraph with explicit non-goals.
- Blast-radius summary: affected files per module plus the external-consumer list.
- Invariants table: behavior -> enforcing test (including new characterization tests as Step 0).
- The ordered step list, each with GOAL / FILES / VERIFY / ROLLBACK.
- The point of no return called out explicitly, with its pre-written rollback/mitigation plan.

## Rules

- Every step must ship green on its own; no step may depend on a future step to restore correctness.
- No step proceeds without its VERIFY command defined; "looks done" is not verification.
- Old code is deleted only after grep proves zero remaining callers.
- The point of no return executes last (or as late as feasible) and never without a written rollback plan.
- If invariant coverage is missing, characterization tests come before any production change.
- This skill produces the plan; do not begin executing refactor steps unless the user approves the plan or asks for execution.
