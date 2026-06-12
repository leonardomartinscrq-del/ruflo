---
name: perf-baseline
description: Before/after benchmarking with honest statistics - build a reproducible benchmark for the hot path, record a multi-run baseline with variance, apply the change, re-run identically, and report the delta against measured noise. Use before claiming any optimization works or when asked to measure performance impact.
---

Measure performance changes credibly. A single timing is an anecdote; this skill builds a repeatable benchmark, captures variance, and only claims a win or regression when the delta clears the noise floor. The deliverable is a number you would defend in a PR description, plus the script anyone can re-run.

## Steps

1. Identify the hot path precisely: which function/endpoint/query, with what input shape and size. If the user only says "it's slow", profile first (`node --cpu-prof`, `python -m cProfile -s cumtime`, `go test -cpuprofile`) and pick the top self-time frame as the target. Write down the target as one sentence.
2. Write a standalone benchmark script under `scripts/bench/` (e.g. `scripts/bench/bench-<target>.mjs` or `.py`) that:
   - Constructs fixed, deterministic input (seeded RNG or checked-in fixture — never live/random data).
   - Warms up: runs the target a few times first and discards those timings (JIT, caches, connection pools).
   - Times N iterations with a monotonic high-resolution clock (`performance.now()`, `time.perf_counter()`), one timing per iteration.
   - Prints every per-run time plus min / median / mean / stddev, and machine-readable JSON.
3. Record the baseline: run the script for N >= 10 measured iterations (use a larger inner loop if a single call is < 1ms, so each sample is meaningful). Compute the coefficient of variation (stddev/mean). If CV > 10%, do not proceed — stabilize first: close watchers/builds, re-run on an idle machine, increase iterations, pin the dataset. Re-measure until CV <= 10% or document why it cannot go lower.
4. Persist the baseline: save the JSON (e.g. `scripts/bench/results/baseline-<target>.json`) including environment metadata — git SHA, runtime version, OS, CPU model, N, and the exact command.
5. Apply the optimization change. Touch nothing else — mixed changes make the comparison unattributable.
6. Re-run the identical script with identical N on the same machine. Save as `after-<target>.json`.
7. Compare honestly: primary metric is the median. The delta is real only if |median_after - median_before| exceeds 2x the larger stddev, or the [min, max] ranges do not overlap. Otherwise the result is "within noise" — report exactly that.
8. Sanity-check correctness: the optimized path must still pass the relevant tests; a fast wrong answer is a regression. Run the suite covering the target.
9. Report the delta as both percentage and absolute time, with both distributions shown, and an explicit noise assessment sentence.

## Output

- The benchmark script path (kept in the repo, re-runnable by anyone).
- Baseline and after JSON result paths.
- Comparison table: min / median / mean / stddev / CV for before and after, N, environment.
- Verdict sentence, one of: "improved by X% (median A -> B, exceeds 2-sigma noise)", "regressed by X%", or "within noise — no claim".

## Rules

- REFUSE to conclude anything from a single run; minimum 10 measured iterations per side.
- Same machine, same N, same input, same script for both sides — no exceptions.
- Median over mean for the headline number; means are outlier-sensitive.
- Report regressions and null results as readily as wins; never round noise into a victory.
- Never benchmark with unrelated heavy processes running; note any environmental caveats in the report.
- Correctness tests must pass on the optimized code before any performance claim is made.
